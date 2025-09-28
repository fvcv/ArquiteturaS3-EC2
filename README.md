# ArquiteturaS3-EC2
=> graph TB
    %% Definindo estilos
    classDef s3Class fill:#ff9900,stroke:#333,stroke-width:2px,color:#fff
    classDef ec2Class fill:#ff6600,stroke:#333,stroke-width:2px,color:#fff  
    classDef lambdaClass fill:#ff9900,stroke:#333,stroke-width:2px,color:#000
    classDef userClass fill:#4CAF50,stroke:#333,stroke-width:2px,color:#fff
    classDef apiClass fill:#2196F3,stroke:#333,stroke-width:2px,color:#fff

    %% Componentes
    User[👤 Usuário]
    API[🌐 API Gateway]
    Lambda[⚡ Lambda Function<br/>Processamento]
    S3[(🪣 S3 Bucket<br/>Armazenamento)]
    EC2[🖥️ EC2 Instance<br/>Aplicação Web]
    
    %% Conexões e fluxo
    User -->|1. Requisição HTTP| API
    API -->|2. Trigger| Lambda
    Lambda -->|3. Processa dados| Lambda
    Lambda -->|4. Armazena arquivos| S3
    Lambda -->|5. Envia dados| EC2
    EC2 -->|6. Lê arquivos| S3
    S3 -->|7. Event notification| Lambda
    EC2 -->|8. Resposta| User
    
    %% Aplicando estilos
    class User userClass
    class API apiClass
    class Lambda lambdaClass
    class S3 s3Class
    class EC2 ec2Class
