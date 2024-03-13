<h1>Aplicações Mult-Tenant com Entity Framework Core</h1>

> O conteúdo também foi organizado nos **commits**

<!--#region Sumário -->

<!--#region Imersão -->

<details><summary>Imersão</summary>

<ul>
    <li><a href="#mt-01">Apresentação</a></li>
    <li><a href="#mt-02">Entendendo o cenário</a></li>
    <li><a href="#mt-03">Mult Tenant</a></li>
    <li><a href="#mt-04">Múltiplos Apps, múltiplos bancos, múltiplos projetos</a></li>
    <li><a href="#mt-05">Compartilhando o Codebase</a></li>
    <li><a href="#mt-06">OOP e múltiplas regras de negócio</a></li>
    <li><a href="#mt-07">Mesmo App múltiplos bancos</a></li>
    <li><a href="#mt-08">Trabalhando com múltiplos bancos no EF Core</a></li>
    <li><a href="#mt-09">Alterando a Connection String dinamicamente</a></li>
    <li><a href="#mt-10">O cenário Mult Tenant</a></li>
    <li><a href="#mt-11">Implementando Mult Tenant com EF Core</a></li>
    <li><a href="#mt-12">Conclusão</a></li>
</ul>

</details>

<!--#endregion -->

<!--#endregion -->

<!--#region Imersão -->

<h2>Imersão</h2>

<!--#region Apresentação -->

<details id="mt-01"><summary>Apresentação</summary>

<br/>

> Mult-Tenant: Suportando múltiplos clientes de forma saudável

- Escalável
- SaaS

</details>

<!--#endregion -->

<!--#region Entendendo o cenário -->

<details id="mt-02"><summary>Entendendo o cenário</summary>

<br/>

Objetivos:
- Entender sobre Mult-Tenant
- Múltiplos clientes com mesmo codebase
- Múltiplos Apps
- Múltiplos bancos

### Mult Tenant

**Tenant**: Inquilino (cliente)

Cenário:
- Você precisa suportar múltiplos clientes?
    - Não vai ser tranquilo
    - Todos os casos tem pontos positivos e negativos
    - Cuidado com segurança
    - Escalabilidade de negócio
    - Alinhamento com C-Level

</details>

<!--#endregion -->

<!--#region Mult Tenant -->

<details id="mt-03"><summary>Mult Tenant</summary>

<br/>

### O que é?

**SaaS e Mult-Tenant**:
- Quer paz? Vá para o **PaaS** (ou **SaaS**)
- Software como serviços
- Escalável
- Permite adesão rápida e sem burocracia
- Suporta múltiplos clientes (inquilinos)

</details>

<!--#endregion -->

<!--#region Múltiplos Apps, múltiplos bancos, múltiplos projetos -->

<details id="mt-04"><summary>Múltiplos Apps, múltiplos bancos, múltiplos projetos</summary>

<br/>

### Muitos Apps

> Cenário mais caótico

**Um cenário comum**:
- Um App para cada cliente
- Cada App com seu banco de dados
- Cada App é um projeto separado
- Nível de caos: 100%

**Quando escala**:
- Quanto mais clientes, mais apps
- Mais customizações
- Mais time necessário
- Mais banco
- Mais deployments
    - CI/CD fica complexo ou não existe
- Mais caos!

</details>

<!--#endregion -->

<!--#region Compartilhando o Codebase -->

<details id="mt-05"><summary> Compartilhando o Codebase</summary>

<br/>

Múltiplos Apps, múltiplo bancos, mesmo codebase

> O cenário melhora um pouco

### Mesmo codebase

**Apenas um projeto**:
- Deployment para múltiplos ambientes/endpoints
- Mesmo código para todos os cliente
- Bancos separados
- Nível de caos: 70%

> Mais customização, mais trabalho

### Muitos clientes, muitas regras...

**Orientação a objetos**:
- Crie classes e regras bases
- Use bem abstração
- Crie derivações destas regras para cada cliente
- Carregue estas derivações através de **Factories** (**Factory Method: Pattern**)
- **Clean Code** é seu melhor amigo

**Feature Flag**:
- Permite liberar features específicas para determinados clientes
- Não é para ser usado para regras de negócio
- Cuidado para não virar bola de neve

</details>

<!--#endregion -->

<!--#region OOP e múltiplas regras de negócio -->

<details id="mt-06"><summary> OOP e múltiplas regras de negócio</summary>

<br/>

### DEMO

Gerenciando múltiplas regras de negócio

[Demo 1](./Assets/Código%20Fonte/2809-main/Demo%2001/)

O método estático **CalculaICMS** com múltiplos IFs aumenta a complexidade ciclomática do código.

Poderia ser utilizado sobrescrita de métodos também com **virtual** e **override**

</details>

<!--#endregion -->


<!--#region -->

<details id=""><summary></summary>

<br/>

</details>

<!--#endregion -->

<!--#endregion -->