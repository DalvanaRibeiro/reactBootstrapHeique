Oi Heique, rapidamente para testar tua ideia pode seguir os seguintes passos.



## Agora, acho que como exemplo mais básico podemos tentar o seguinte:
## iniciando um projeto

npm create vite@latest meu-app --template react
cd meu-app
npm install


## Instalando o bootstrap:
npm install bootstrap

## No main.tsx adicione:

import 'bootstrap/dist/css/bootstrap.min.css';


## Agora, na pasta components, crie o arquivo do formulario (LoginForm.ts):


import React, { useState } from 'react';

const LoginForm: React.FC = () => {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  // Função chamada no envio do formulário
  const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault(); // previne reload da página
    console.log('Login com:', { email, password });
  };

  return (
    // Contêiner flexível, centralizado vertical e horizontalmente, com altura total da viewport
    // Com o **Bootstrap usamos as seguintes classes Heique:** d-flex, align-items-center, justify-content-center, vh-100, bg-light
    <div className="d-flex align-items-center justify-content-center vh-100 bg-light">
      
      {/* Card do Bootstrap: painel com sombra, padding e bordas arredondadas */}
      {/* Usamos também max-width para limitar o tamanho do card */}
      {/* Classes Bootstrap: card, p-4 (padding), shadow (sombra), rounded (bordas arredondadas) */}
      <div className="card p-4 shadow rounded" style={{ width: '100%', maxWidth: '400px' }}>
        
        {/* Corpo do card */}
        <div className="card-body">
          
          {/* Título centralizado com margem inferior */}
          {/* Bootstrap classes: card-title, text-center, mb-4 */}
          <h4 className="card-title text-center mb-4">Login</h4>

          {/* Formulário */}
          <form onSubmit={handleSubmit}>
            
            {/* Grupo do input email */}
            {/* Bootstrap classes: mb-3 (margem inferior) */}
            <div className="mb-3">
              {/* Label estilizado */}
              {/* Bootstrap: form-label */}
              <label htmlFor="email" className="form-label">Email</label>

              {/* Input com estilo Bootstrap */}
              {/* Bootstrap: form-control */}
              <input
                type="email"
                id="email"
                className="form-control"
                placeholder="Digite seu email"
                value={email}
                onChange={(e) => setEmail(e.target.value)}
                required
              />
            </div>

            {/* Grupo do input senha */}
            <div className="mb-3">
              <label htmlFor="password" className="form-label">Senha</label>
              <input
                type="password"
                id="password"
                className="form-control"
                placeholder="Digite sua senha"
                value={password}
                onChange={(e) => setPassword(e.target.value)}
                required
              />
            </div>

            {/* Botão que ocupa toda largura do container pai */}
            {/* Bootstrap classes: d-grid para grid layout e btn, btn-primary para botão */}
            <div className="d-grid">
              <button type="submit" className="btn btn-primary">
                Entrar
              </button>
            </div>

          </form>
        </div>
      </div>
    </div>
  );
};

export default LoginForm;


## No App.tsx, chame ele:


import LoginForm from './components/LoginForm';

function App() {
  return <LoginForm />; // chamando o componente
}

export default App;
  ## As vezes acusa erro no arquivo tsconfig.App.json, neste caso comente a linha do erro:

      //"erasableSyntaxOnly": true,

## Rode com:

npm run dev
