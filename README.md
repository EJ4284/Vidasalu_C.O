# Vidasalu_C.O
Pagina de salud y ejercios
<div class="imc-calculator">
  <h2>Calculadora de IMC + Plan Integral</h2>
  <form id="imc-form">
    <div class="form-group">
      <label for="weight">Peso (kg):</label>
      <input type="number" id="weight" step="0.1" min="20" max="300" required>
    </div>
    <div class="form-group">
      <label for="height">Altura (cm):</label>
      <input type="number" id="height" min="100" max="250" required>
    </div>
    <div class="form-group">
      <label for="activity-level">Nivel de actividad:</label>
      <select id="activity-level" class="form-control">
        <option value="sedentary">Sedentario</option>
        <option value="light">Ligero (ejercicio 1-3 días/semana)</option>
        <option value="moderate">Moderado (ejercicio 3-5 días/semana)</option>
        <option value="active">Activo (ejercicio 6-7 días/semana)</option>
        <option value="athlete">Atleta (entrenamiento intenso diario)</option>
      </select>
    </div>
    <button type="submit">Obtener mi plan personalizado</button>
  </form>
  
  <div id="imc-result" class="result-container" style="display: none;">
    <h3>Resultado:</h3>
    <p>Tu IMC es: <span id="imc-value">0</span></p>
    <p>Clasificación: <span id="imc-classification">-</span></p>
    <div id="imc-scale" class="scale">
      <div class="scale-labels">
        <span>Bajo peso</span>
        <span>Normal</span>
        <span>Sobrepeso</span>
        <span>Obesidad</span>
      </div>
      <div class="scale-bar">
        <div class="indicator" id="imc-indicator"></div>
      </div>
      <div class="scale-numbers">
        <span>18.5</span>
        <span>25</span>
        <span>30</span>
      </div>
    </div>
    
    <div class="plan-tabs">
      <button class="tab-btn active" data-tab="nutrition">Nutrición</button>
      <button class="tab-btn" data-tab="exercise">Ejercicios</button>
      <button class="tab-btn" data-tab="lifestyle">Estilo de Vida</button>
    </div>
    
    <div id="nutrition" class="tab-content active">
      <div class="nutrition-tabs">
        <button class="subtab-btn active" data-subtab="breakfast">Desayunos</button>
        <button class="subtab-btn" data-subtab="lunch">Almuerzos</button>
        <button class="subtab-btn" data-subtab="dinner">Cenas</button>
      </div>
      
      <div id="breakfast" class="subtab-content active">
        <h4><i class="icon">🍳</i> Recomendaciones de Desayuno</h4>
        <div id="breakfast-content" class="recommendation-content"></div>
      </div>
      
      <div id="lunch" class="subtab-content">
        <h4><i class="icon">🍲</i> Recomendaciones de Almuerzo</h4>
        <div id="lunch-content" class="recommendation-content"></div>
      </div>
      
      <div id="dinner" class="subtab-content">
        <h4><i class="icon">🥗</i> Recomendaciones de Cena</h4>
        <div id="dinner-content" class="recommendation-content"></div>
      </div>
    </div>
    
    <div id="exercise" class="tab-content">
      <h4><i class="icon">💪</i> Plan de Ejercicios Personalizado</h4>
      <div id="exercise-content" class="recommendation-content"></div>
    </div>
    
    <div id="lifestyle" class="tab-content">
      <h4><i class="icon">🌿</i> Recomendaciones de Estilo de Vida</h4>
      <div id="lifestyle-content" class="recommendation-content"></div>
    </div>
  </div>
</div>

<style>
  .imc-calculator {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    max-width: 700px;
    margin: 30px auto;
    padding: 30px;
    border-radius: 15px;
    background: linear-gradient(135deg, #f9f9f9 0%, #eef2f5 100%);
    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
    border: 1px solid #e0e0e0;
  }
  
  h2 {
    color: #2c3e50;
    text-align: center;
    margin-bottom: 30px;
    font-size: 28px;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 10px;
    font-weight: 600;
    color: #34495e;
    font-size: 16px;
  }
  
  input, select {
    width: 100%;
    padding: 14px;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-sizing: border-box;
    font-size: 16px;
    transition: all 0.3s;
    background-color: white;
  }
  
  input:focus, select:focus {
    border-color: #4CAF50;
    outline: none;
    box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
  }
  
  button[type="submit"] {
    background: linear-gradient(to right, #4CAF50, #2E8B57);
    color: white;
    padding: 16px 24px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 18px;
    width: 100%;
    transition: all 0.3s;
    font-weight: 600;
    margin-top: 15px;
    letter-spacing: 0.5px;
  }
  
  button[type="submit"]:hover {
    background: linear-gradient(to right, #45a049, #267445);
    transform: translateY(-3px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
  
  .result-container {
    margin-top: 35px;
    padding: 30px;
    background-color: white;
    border-radius: 12px;
    box-shadow: 0 3px 15px rgba(0,0,0,0.05);
    animation: fadeIn 0.6s ease-out;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  .scale {
    margin-top: 30px;
  }
  
  .scale-labels {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    margin-bottom: 10px;
    color: #555;
    font-weight: 500;
  }
  
  .scale-bar {
    height: 25px;
    background: linear-gradient(to right, #3498db, #2ecc71, #f39c12, #e74c3c);
    border-radius: 12px;
    position: relative;
    margin-bottom: 10px;
    overflow: hidden;
  }
  
  .indicator {
    position: absolute;
    top: -7px;
    width: 14px;
    height: 39px;
    background-color: #2c3e50;
    transform: translateX(-7px);
    border-radius: 4px;
    z-index: 2;
    box-shadow: 0 0 7px rgba(0,0,0,0.2);
  }
  
  .scale-numbers {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    margin-top: 8px;
    color: #555;
  }
  
  #imc-value {
    font-weight: bold;
    font-size: 24px;
    color: #2c3e50;
  }
  
  #imc-classification {
    font-weight: bold;
    text-transform: capitalize;
    color: #2c3e50;
    font-size: 20px;
  }
  
  .plan-tabs {
    display: flex;
    border-bottom: 2px solid #e0e0e0;
    margin: 30px 0 20px;
  }
  
  .tab-btn {
    padding: 14px 24px;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 16px;
    font-weight: 600;
    color: #7f8c8d;
    position: relative;
    transition: all 0.3s;
  }
  
  .tab-btn.active {
    color: #2c3e50;
  }
  
  .tab-btn.active:after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 4px;
    background: linear-gradient(to right, #4CAF50, #2E8B57);
    border-radius: 4px 4px 0 0;
  }
  
  .tab-btn:hover:not(.active) {
    color: #4CAF50;
    background-color: #f5f5f5;
  }
  
  .tab-content {
    display: none;
    animation: fadeIn 0.5s ease-out;
  }
  
  .tab-content.active {
    display: block;
  }
  
  .nutrition-tabs {
    display: flex;
    border-bottom: 1px solid #e0e0e0;
    margin-bottom: 20px;
  }
  
  .subtab-btn {
    padding: 10px 16px;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 14px;
    font-weight: 500;
    color: #7f8c8d;
    position: relative;
    transition: all 0.3s;
    margin-right: 5px;
    border-radius: 6px 6px 0 0;
  }
  
  .subtab-btn.active {
    color: #2c3e50;
    background-color: #f5f5f5;
  }
  
  .subtab-btn:hover:not(.active) {
    color: #4CAF50;
    background-color: #f9f9f9;
  }
  
  .subtab-content {
    display: none;
  }
  
  .subtab-content.active {
    display: block;
  }
  
  .recommendation-content {
    background-color: #f8f9fa;
    border-radius: 10px;
    padding: 25px;
    margin-top: 15px;
  }
  
  .recommendation-content h4 {
    color: #2c3e50;
    margin-top: 0;
    margin-bottom: 20px;
    font-size: 20px;
    border-bottom: 1px solid #e0e0e0;
    padding-bottom: 12px;
    display: flex;
    align-items: center;
  }
  
  .recommendation-content h5 {
    color: #2c3e50;
    margin-top: 25px;
    margin-bottom: 15px;
    font-size: 18px;
  }
  
  .recommendation-content ul {
    padding-left: 25px;
    margin-bottom: 0;
  }
  
  .recommendation-content li {
    margin-bottom: 15px;
    line-height: 1.6;
    color: #34495e;
  }
  
  .recommendation-content strong {
    color: #2c3e50;
  }
  
  .icon {
    margin-right: 12px;
    font-size: 22px;
  }
  
  .exercise-plan {
    margin-bottom: 25px;
  }
  
  .exercise-plan h5 {
    display: flex;
    align-items: center;
  }
  
  .exercise-plan ul {
    padding-left: 20px;
  }
  
  .exercise-plan li {
    margin-bottom: 10px;
    position: relative;
    padding-left: 25px;
  }
  
  .exercise-plan li:before {
    content: '→';
    position: absolute;
    left: 0;
    color: #4CAF50;
  }
  
  .warning-note {
    background-color: #fff8e1;
    border-left: 4px solid #ffc107;
    padding: 15px;
    margin: 20px 0;
    border-radius: 0 6px 6px 0;
  }
  
  .warning-note h5 {
    color: #ff9800;
    margin-top: 0;
  }
  
  .week-plan {
    margin-top: 25px;
  }
  
  .day-plan {
    background-color: white;
    border-radius: 8px;
    padding: 15px;
    margin-bottom: 15px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
  }
  
  .day-plan h6 {
    margin-top: 0;
    margin-bottom: 15px;
    color: #4CAF50;
    font-size: 16px;
    display: flex;
    align-items: center;
  }
  
  .day-plan h6 i {
    margin-right: 10px;
  }
  
  @media (max-width: 768px) {
    .imc-calculator {
      padding: 20px;
      margin: 15px;
    }
    
    .plan-tabs, .nutrition-tabs {
      flex-wrap: wrap;
    }
    
    .tab-btn, .subtab-btn {
      flex: 1;
      min-width: 120px;
      padding: 10px 5px;
      font-size: 14px;
      text-align: center;
    }
    
    .recommendation-content {
      padding: 15px;
    }
  }
</style>

<script>
  document.getElementById('imc-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const weight = parseFloat(document.getElementById('weight').value);
    const height = parseInt(document.getElementById('height').value) / 100;
    const activityLevel = document.getElementById('activity-level').value;
    
    if (weight && height) {
      const imc = weight / (height * height);
      const roundedImc = Math.round(imc * 10) / 10;
      
      document.getElementById('imc-value').textContent = roundedImc;
      
      let classification = '';
      let indicatorPosition = 0;
      let breakfastRec = '';
      let lunchRec = '';
      let dinnerRec = '';
      let exerciseRec = '';
      let lifestyleRec = '';
      
      if (imc < 18.5) {
        classification = 'Bajo peso';
        indicatorPosition = (imc / 18.5) * 25;
        
        // Nutrición
        breakfastRec = `<h5>Para aumentar energía y nutrientes</h5>
          <ul>
            <li><strong>Avena hipercalórica:</strong> Avena cocida con leche entera, miel, nueces, almendras y trozos de plátano</li>
            <li><strong>Tostadas integrales con aguacate y huevo:</strong> Pan integral con aguacate machacado, huevos revueltos y queso fresco</li>
            <li><strong>Batido energético:</strong> Leche entera, plátano, mantequilla de maní, avena y miel</li>
          </ul>`;
        
        lunchRec = `<h5>Almuerzos nutritivos y calóricos</h5>
          <ul>
            <li><strong>Pasta integral con atún:</strong> Pasta integral con atún al natural, aceite de oliva, tomate cherry y espinacas</li>
            <li><strong>Arroz con pollo y aguacate:</strong> Arroz integral con pechuga de pollo a la plancha, aguacate y vegetales salteados</li>
            <li><strong>Ensalada de quinoa:</strong> Quinoa con garbanzos, aguacate, tomate, pepino y aderezo de tahini</li>
          </ul>`;
        
        dinnerRec = `<h5>Cenas nutritivas y fáciles de digerir</h5>
          <ul>
            <li><strong>Salmón al horno:</strong> Salmón con patatas asadas y brócoli al vapor</li>
            <li><strong>Tortilla española:</strong> Tortilla de patata con cebolla y pan integral</li>
            <li><strong>Sándwich nutritivo:</strong> Pan integral con pechuga de pavo, queso y aguacate</li>
          </ul>`;
        
        // Ejercicios
        exerciseRec = `<div class="exercise-plan">
          <h5><i class="icon">🏋️‍♂️</i> Plan de Entrenamiento para Ganar Masa Muscular</h5>
          <p>Objetivo principal: Aumentar masa muscular de forma equilibrada.</p>
          
          <div class="week-plan">
            <div class="day-plan">
              <h6><i>📅</i> Lunes - Tren Superior</h6>
              <ul>
                <li>Press de banca: 4 series × 8-12 repeticiones</li>
                <li>Dominadas asistidas: 3 series × 6-10 repeticiones</li>
                <li>Remo con barra: 3 series × 10-12 repeticiones</li>
                <li>Press militar: 3 series × 8-10 repeticiones</li>
                <li>Curl de bíceps: 3 series × 12 repeticiones</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Miércoles - Tren Inferior</h6>
              <ul>
                <li>Sentadillas: 4 series × 8-12 repeticiones</li>
                <li>Peso muerto rumano: 3 series × 8-10 repeticiones</li>
                <li>Prensa: 3 series × 10-12 repeticiones</li>
                <li>Elevación de talones: 3 series × 15 repeticiones</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Viernes - Full Body</h6>
              <ul>
                <li>Press militar: 3 series × 8-10 repeticiones</li>
                <li>Dominadas: 3 series × 6-10 repeticiones</li>
                <li>Sentadillas búlgaras: 3 series × 10 por pierna</li>
                <li>Plancha abdominal: 3 series × 30 segundos</li>
              </ul>
            </div>
          </div>
          
          <div class="warning-note">
            <h5>Recomendaciones importantes:</h5>
            <ul>
              <li>Descansa 60-90 segundos entre series</li>
              <li>Progresivamente aumenta el peso</li>
              <li>Combina con una dieta hipercalórica saludable</li>
              <li>Descansa 1-2 días entre sesiones de mismo grupo muscular</li>
            </ul>
          </div>
        </div>`;
        
        // Estilo de vida
        lifestyleRec = `<h5>Consejos para aumentar peso saludablemente</h5>
          <ul>
            <li><strong>Come con frecuencia:</strong> 5-6 comidas al día para aumentar la ingesta calórica</li>
            <li><strong>Elige alimentos densos en nutrientes:</strong> Frutos secos, aguacate, lácteos enteros, carnes magras</li>
            <li><strong>Entrena con pesas:</strong> El ejercicio de fuerza estimula el apetito y el crecimiento muscular</li>
            <li><strong>Descansa adecuadamente:</strong> Duerme 7-9 horas para permitir la recuperación muscular</li>
            <li><strong>Controla el estrés:</strong> El estrés crónico puede afectar tu apetito y metabolismo</li>
          </ul>`;
        
      } else if (imc < 25) {
        classification = 'Peso normal';
        indicatorPosition = 25 + ((imc - 18.5) / (25 - 18.5)) * 25;
        
        // Nutrición
        breakfastRec = `<h5>Para mantener tu peso saludable</h5>
          <ul>
            <li><strong>Bowl de yogur y frutas:</strong> Yogur natural con fresas, arándanos, semillas de chía y granola</li>
            <li><strong>Tortilla de espinacas:</strong> Tortilla de 2 huevos con espinacas frescas, tomate y pan integral</li>
            <li><strong>Smoothie verde:</strong> Espinaca, plátano, leche de almendras y mantequilla de maní</li>
          </ul>`;
        
        lunchRec = `<h5>Almuerzos equilibrados</h5>
          <ul>
            <li><strong>Ensalada completa:</strong> Lechuga, quinoa, pollo a la plancha, aguacate y nueces</li>
            <li><strong>Pescado al horno:</strong> Merluza o salmón con arroz integral y vegetales al vapor</li>
            <li><strong>Wraps integrales:</strong> Tortillas integrales con pavo, vegetales frescos y guacamole</li>
          </ul>`;
        
        dinnerRec = `<h5>Cenas ligeras pero nutritivas</h5>
          <ul>
            <li><strong>Crema de verduras:</strong> Calabaza, zanahoria o brócoli con trozos de pavo</li>
            <li><strong>Revuelto de setas:</strong> Huevo con champiñones y espárragos trigueros</li>
            <li><strong>Salmón a la plancha:</strong> Con espárragos y puré de coliflor</li>
          </ul>`;
        
        // Ejercicios
        exerciseRec = `<div class="exercise-plan">
          <h5><i class="icon">🏃‍♀️</i> Plan de Entrenamiento para Mantenimiento y Salud</h5>
          <p>Objetivo principal: Mantener condición física general y salud.</p>
          
          <div class="week-plan">
            <div class="day-plan">
              <h6><i>📅</i> Lunes - Cardio + Fuerza Superior</h6>
              <ul>
                <li>Carrera suave o bicicleta: 30 minutos</li>
                <li>Flexiones: 3 series × 12-15 repeticiones</li>
                <li>Dominadas: 3 series × 6-10 repeticiones</li>
                <li>Plancha abdominal: 3 series × 30-45 segundos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Miércoles - Yoga/Movilidad</h6>
              <ul>
                <li>Sesión de yoga o movilidad: 45 minutos</li>
                <li>Ejercicios de respiración y estiramientos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Viernes - Fuerza Inferior + Cardio</h6>
              <ul>
                <li>Sentadillas: 3 series × 12-15 repeticiones</li>
                <li>Zancadas: 3 series × 10 por pierna</li>
                <li>Elevación de talones: 3 series × 15 repeticiones</li>
                <li>Natación o elíptica: 20 minutos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Sábado - Actividad Recreativa</h6>
              <ul>
                <li>Senderismo, paseo en bicicleta o deporte de equipo</li>
                <li>Duración: 45-60 minutos</li>
              </ul>
            </div>
          </div>
          
          <div class="warning-note">
            <h5>Recomendaciones importantes:</h5>
            <ul>
              <li>Varía tus actividades para evitar aburrimiento</li>
              <li>Escucha a tu cuerpo y ajusta intensidad según necesidad</li>
              <li>Combina ejercicio aeróbico y de fuerza</li>
              <li>Mantén una dieta equilibrada acorde a tu gasto energético</li>
            </ul>
          </div>
        </div>`;
        
        // Estilo de vida
        lifestyleRec = `<h5>Consejos para mantener un peso saludable</h5>
          <ul>
            <li><strong>Mantén la variedad:</strong> Consume diferentes grupos de alimentos para obtener todos los nutrientes</li>
            <li><strong>Hidrátate bien:</strong> Bebe al menos 2 litros de agua al día</li>
            <li><strong>Combina ejercicio aeróbico y anaeróbico:</strong> Para salud cardiovascular y muscular</li>
            <li><strong>Controla porciones:</strong> Aunque tengas peso normal, evita excesos</li>
            <li><strong>Chequeos regulares:</strong> Realiza controles médicos anuales</li>
          </ul>`;
        
      } else if (imc < 30) {
        classification = 'Sobrepeso';
        indicatorPosition = 50 + ((imc - 25) / (30 - 25)) * 25;
        
        // Nutrición
        breakfastRec = `<h5>Para controlar el peso</h5>
          <ul>
            <li><strong>Huevos pochados con espárragos:</strong> 1-2 huevos sobre espárragos salteados con aguacate</li>
            <li><strong>Porridge de chía:</strong> Semillas de chía remojadas en leche desnatada con canela y frutos rojos</li>
            <li><strong>Tostada integral con queso cottage:</strong> Pan integral con queso cottage, tomate y pimienta</li>
          </ul>`;
        
        lunchRec = `<h5>Almuerzos saciantes bajos en calorías</h5>
          <ul>
            <li><strong>Ensalada de garbanzos:</strong> Garbanzos con pepino, tomate, cebolla morada y vinagreta de limón</li>
            <li><strong>Pollo al curry light:</strong> Pechuga de pollo con curry light, leche de coco light y vegetales</li>
            <li><strong>Calabacines rellenos:</strong> Calabacín relleno de carne magra picada y quinoa</li>
          </ul>`;
        
        dinnerRec = `<h5>Cenas ligeras y proteicas</h5>
          <ul>
            <li><strong>Sopa de miso con tofu:</strong> Sopa japonesa ligera con tofu y algas</li>
            <li><strong>Tortilla de claras:</strong> Con espinacas y champiñones</li>
            <li><strong>Pescado blanco al horno:</strong> Con pimentón y limón, acompañado de brócoli</li>
          </ul>`;
        
        // Ejercicios
        exerciseRec = `<div class="exercise-plan">
          <h5><i class="icon">🚴‍♂️</i> Plan de Entrenamiento para Pérdida de Grasa</h5>
          <p>Objetivo principal: Reducir porcentaje de grasa manteniendo masa muscular.</p>
          
          <div class="week-plan">
            <div class="day-plan">
              <h6><i>📅</i> Lunes - Cardio Intervalado</h6>
              <ul>
                <li>Calentamiento: 10 minutos caminata rápida</li>
                <li>Intervalos (8 rondas): 1 minuto carrera intensa + 2 minutos caminata</li>
                <li>Enfriamiento: 5 minutos caminata suave</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Martes - Fuerza Full Body</h6>
              <ul>
                <li>Sentadillas: 3 series × 12-15 repeticiones</li>
                <li>Flexiones (en rodillas si necesario): 3 series × 10-12 repeticiones</li>
                <li>Remo con mancuernas: 3 series × 12 repeticiones</li>
                <li>Plancha: 3 series × 30 segundos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Jueves - Cardio Estable</h6>
              <ul>
                <li>Caminata rápida, bicicleta o elíptica: 45 minutos a ritmo constante</li>
                <li>Intensidad moderada (poder mantener conversación)</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Sábado - Circuito Funcional</h6>
              <ul>
                <li>Estaciones (45 segundos trabajo, 15 descanso, 3 rondas):</li>
                <li>Sentadillas con peso corporal</li>
                <li>Flexiones (modificadas si necesario)</li>
                <li>Zancadas alternadas</li>
                <li>Remo con banda elástica</li>
                <li>Plancha lateral</li>
              </ul>
            </div>
          </div>
          
          <div class="warning-note">
            <h5>Recomendaciones importantes:</h5>
            <ul>
              <li>Combina dieta hipocalórica con ejercicio regular</li>
              <li>Prioriza proteínas para mantener masa muscular</li>
              <li>Progresivamente aumenta intensidad del ejercicio</li>
              <li>Descansa al menos 1 día completo a la semana</li>
              <li>Bebe agua antes, durante y después del ejercicio</li>
            </ul>
          </div>
        </div>`;
        
        // Estilo de vida
        lifestyleRec = `<h5>Consejos para reducir peso saludablemente</h5>
          <ul>
            <li><strong>Control de porciones:</strong> Usa platos más pequeños y come despacio</li>
            <li><strong>Hidratación:</strong> Bebe agua antes de las comidas para reducir apetito</li>
            <li><strong>Sueño adecuado:</strong> Duerme 7-8 horas para regular hormonas del apetito</li>
            <li><strong>Reduce estrés:</strong> El estrés aumenta cortisol y acumulación de grasa abdominal</li>
            <li><strong>Movimiento diario:</strong> Aumenta NEAT (actividad no relacionada con ejercicio)</li>
          </ul>`;
        
      } else {
        classification = 'Obesidad';
        indicatorPosition = 75 + ((Math.min(imc, 40) - 30) / (40 - 30)) * 25;
        
        // Nutrición
        breakfastRec = `<h5>Para comenzar el día de forma saludable</h5>
          <ul>
            <li><strong>Revuelto de claras:</strong> 3 claras de huevo con espinacas, champiñones y tomate cherry</li>
            <li><strong>Yogur desnatado con semillas:</strong> Yogur griego 0% con semillas de linaza y 5 almendras</li>
            <li><strong>Pan integral con pavo:</strong> 1 rebanada de pan integral con pechuga de pavo y té verde</li>
          </ul>`;
        
        lunchRec = `<h5>Almuerzos saludables para control de peso</h5>
          <ul>
            <li><strong>Ensalada de lentejas:</strong> Lentejas con zanahoria, apio y vinagreta de mostaza</li>
            <li><strong>Pechuga a la plancha:</strong> Con puré de coliflor y ensalada verde</li>
            <li><strong>Crema de calabacín:</strong> Sin patata, con trozos de pollo desmenuzado</li>
          </ul>`;
        
        dinnerRec = `<h5>Cenas muy ligeras y nutritivas</h5>
          <ul>
            <li><strong>Sopa de verduras:</strong> Con trozos de pavo o pollo</li>
            <li><strong>Ensalada de atún:</strong> Lechuga, atún al natural, pepino y vinagre</li>
            <li><strong>Pescado blanco al papillote:</strong> Con limón y especias, acompañado de espárragos</li>
          </ul>`;
        
        // Ejercicios
        exerciseRec = `<div class="exercise-plan">
          <h5><i class="icon">🧘‍♀️</i> Plan de Inicio para Personas con Obesidad</h5>
          <p>Objetivo principal: Comenzar actividad física de forma segura y progresiva.</p>
          
          <div class="week-plan">
            <div class="day-plan">
              <h6><i>📅</i> Lunes - Caminata + Movilidad</h6>
              <ul>
                <li>Caminata suave: 10-15 minutos</li>
                <li>Ejercicios de movilidad articular: 10 minutos</li>
                <li>Estiramientos suaves: 5 minutos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Miércoles - Ejercicios en Silla</h6>
              <ul>
                <li>Levantamientos de piernas sentado: 3 series × 10 repeticiones</li>
                <li>Press de hombros con botellas de agua: 3 series × 8 repeticiones</li>
                <li>Flexiones de brazos contra pared: 3 series × 5 repeticiones</li>
                <li>Respiración diafragmática: 5 minutos</li>
              </ul>
            </div>
            
            <div class="day-plan">
              <h6><i>📅</i> Viernes - Caminata + Ejercicios en Piscina</h6>
              <ul>
                <li>Caminata en agua: 15 minutos</li>
                <li>Ejercicios de levantamiento de piernas en agua</li>
                <li>Movimientos suaves de brazos en agua</li>
              </ul>
            </div>
          </div>
          
          <div class="warning-note">
            <h5>Recomendaciones importantes:</h5>
            <ul>
              <li>Comienza muy gradualmente para evitar lesiones</li>
              <li>Prioriza ejercicios de bajo impacto (natación, bicicleta reclinada)</li>
              <li>Consulta siempre con médico antes de comenzar</li>
              <li>Enfócate primero en nutrición, luego aumenta ejercicio progresivamente</li>
              <li>Escucha a tu cuerpo y detente si sientes dolor</li>
            </ul>
          </div>
        </div>`;
        
        // Estilo de vida
        lifestyleRec = `<h5>Consejos para manejar la obesidad</h5>
          <ul>
            <li><strong>Cambios graduales:</strong> Implementa cambios pequeños y sostenibles</li>
            <li><strong>Apoyo profesional:</strong> Busca ayuda de nutricionista y médico</li>
            <li><strong>Actividad diaria:</strong> Comienza con pequeños aumentos en movimiento diario</li>
            <li><strong>Control médico:</strong> Realiza chequeos de presión, glucosa y colesterol</li>
            <li><strong>Grupos de apoyo:</strong> Considera unirte a grupos para manejo de peso</li>
          </ul>`;
      }
      
      // Ajustar según nivel de actividad
      if (activityLevel !== 'sedentary') {
        if (classification === 'Bajo peso') {
          exerciseRec += `<div class="warning-note">
            <h5>Nota sobre tu nivel de actividad:</h5>
            <p>Como eres una persona activa, asegúrate de consumir suficientes calorías para compensar tu gasto energético. Considera aumentar las porciones o añadir snacks saludables entre comidas.</p>
          </div>`;
        } else if (classification === 'Sobrepeso' || classification === 'Obesidad') {
          exerciseRec += `<div class="warning-note">
            <h5>Nota sobre tu nivel de actividad:</h5>
            <p>Tu nivel de actividad actual es bueno para mejorar tu salud. Asegúrate de progresar gradualmente en intensidad y duración del ejercicio para evitar lesiones.</p>
          </div>`;
        }
      }
      
      document.getElementById('imc-classification').textContent = classification;
      document.getElementById('imc-indicator').style.left = `${Math.min(100, Math.max(0, indicatorPosition))}%`;
      document.getElementById('breakfast-content').innerHTML = breakfastRec;
      document.getElementById('lunch-content').innerHTML = lunchRec;
      document.getElementById('dinner-content').innerHTML = dinnerRec;
      document.getElementById('exercise-content').innerHTML = exerciseRec;
      document.getElementById('lifestyle-content').innerHTML = lifestyleRec;
      
      document.getElementById('imc-result').style.display = 'block';
      
      // Activar pestañas principales
      const tabBtns = document.querySelectorAll('.tab-btn');
      const tabContents = document.querySelectorAll('.tab-content');
      
      tabBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          tabBtns.forEach(b => b.classList.remove('active'));
          tabContents.forEach(c => c.classList.remove('active'));
          
          btn.classList.add('active');
          document.getElementById(btn.dataset.tab).classList.add('active');
        });
      });
      
      // Activar subpestañas de nutrición
      const subtabBtns = document.querySelectorAll('.subtab-btn');
      const subtabContents = document.querySelectorAll('.subtab-content');
      
      subtabBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          subtabBtns.forEach(b => b.classList.remove('active'));
          subtabContents.forEach(c => c.classList.remove('active'));
          
          btn.classList.add('active');
          document.getElementById(btn.dataset.subtab).classList.add('active');
        });
      });
    }
  });
</script>
