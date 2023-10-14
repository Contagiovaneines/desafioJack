# Desafio Jack - README

Este repositório contém um exemplo de aplicativo web implantado no Kubernetes usando Helm e Minikube.

## Pré-requisitos

- **Minikube**: Certifique-se de ter o Minikube instalado no seu sistema. Consulte as [instruções de instalação](https://minikube.sigs.k8s.io/docs/start/).
- **Helm**: Instale o Helm seguindo as [instruções oficiais](https://helm.sh/docs/intro/install/).

## Passos para Executar

1. **Iniciando o Minikube**

   Abra o terminal e inicie o Minikube com o comando:

   ```bash
   minikube start
   ```

2. **Criando o Helm Chart**

   Crie um diretório para o projeto e gere um chart com o Helm:

   ```bash
   mkdir desafioJack
   cd desafioJack
   helm create webapp1
   ```

3. **Seguindo o Vídeo**

   Siga o vídeo para criar e editar os arquivos conforme as instruções. Você pode copiar e colar os arquivos do diretório `templates-original` ou usar os arquivos do diretório `solution`.

4. **Instalando o Aplicativo**

   No terminal, instale o aplicativo com o Helm:

   ```bash
   helm install mywebapp-release webapp1/ --values mywebapp/values.yaml
   ```

5. **Atualizando o Aplicativo**

   Se desejar atualizar o aplicativo após as modificações, utilize o comando Helm upgrade:

   ```bash
   helm upgrade mywebapp-release webapp1/ --values mywebapp/values.yaml
   ```

6. **Acessando os Serviços**

   Inicie um túnel para acessar os serviços:

   ```bash
   minikube tunnel
   ```

   Observe que acesse [este link](https://minikube.sigs.k8s.io/docs/handbook/accessing/#access-to-ports-1024-on-windows-requires-root-permission) caso encontre problemas de acesso a portas.

7. **Criando Ambientes de Desenvolvimento e Produção**

   Crie namespaces para ambientes de desenvolvimento e produção:

   ```bash
   kubectl create namespace dev
   kubectl create namespace prod
   ```

   Instale o aplicativo em cada ambiente:

   ```bash
   helm install mywebapp-release-dev webapp1/ --values webapp1/values.yaml -f webapp1/values-dev.yaml -n dev
   helm install mywebapp-release-prod webapp1/ --values webapp1/values.yaml -f webapp1/values-prod.yaml -n prod
   ```

8. **Listando Todas as Releases**

   Para listar todas as releases em todos os namespaces, utilize o comando:

   ```bash
   helm ls --all-namespaces
   ```

## Conclusão
