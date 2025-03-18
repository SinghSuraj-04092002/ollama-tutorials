# **Running Ollama on Google Colab with Ngrok**  

This guide walks you through setting up **Ollama** in **Google Colab** using **Ngrok**, allowing you to run large language models (LLMs) in the cloud and access them remotely.  

---

## **🔗 Quick Links**  

- **Jupyter Notebooks**  
  - [Official Ollama Notebook](https://github.com/ollama/ollama/blob/5687f1a0cfa3d2408bfcb04f4342f657f6dada58/examples/jupyter-notebook/ollama.ipynb)  
- **Ngrok**  
  - [Ngrok Website](https://ngrok.com/)  
  - [Guide to Free Static Domains](https://ngrok.com/blog-post/free-static-domains-ngrok-users)  
- **Ollama**  
  - [Official Website](https://ollama.com/)  
  - [Installation Guide](/ollama/install-ollama/README.md)  
- **Google Colab**  
  - [Colab Homepage](https://colab.research.google.com/)  
  - [Colab Pricing](https://colab.research.google.com/signup/pricing)  

---

## **⚙️ What You’ll Need**  

- **Ollama**: A framework for running LLMs locally or in the cloud.  
- **Google Colab**: A cloud-based notebook environment for Python and AI workflows.  
  - Requires a free Google account.  
  - Consider [Colab Pro](https://colab.research.google.com/signup/pricing) for better performance.  
- **Ngrok**: A tool that creates public URLs for local servers.  
  - Sign up for a free account to get an authentication token and a static domain.  

---

## **🚀 Setting Up Ollama on Colab**  

### **Step 1: Get Your Ngrok Authentication Token & Static Domain**  

1. Log in to your [Ngrok account](https://ngrok.com/).  
2. Locate and copy your **Auth Token** from the "Your Auth-Token" section.  
3. (Optional) Set up a **static domain** in the "Domains" section.  

---

### **Step 2: Open the Preconfigured Jupyter Notebook**  

1. Open the given Jupyter notebook in Google Colab.  
2. Ensure you're logged in with your Google account.  

---

### **Step 3: Store Your Ngrok Auth Token in Colab**  

1. In Colab, go to the **Secrets** section.  
2. Add a new secret with the name **`NGROK_AUTH_TOKEN`**.  
3. Paste the **authentication token** from Ngrok into the value field.  
4. Enable notebook access.  
5. Update the final cell in the notebook:  
   - Replace **`<insert-your-static-ngrok-domain-here>`** with your **Ngrok static domain**.  
   - If you don’t have a static domain, **uncomment** line 9 and **comment** line 10.  

---

### **Step 4: Run the Jupyter Notebook**  

1. Execute all cells in the notebook.  
2. If everything is set up correctly, you should see an output like this:  

   ```plaintext
   "started tunnel" obj=tunnels name=command_line addr=http://localhost:11434 url=https://example.ngrok-free.app
   ```

> If using a static Ngrok URL, the output should match your **assigned domain**. If not, a **random URL** will be generated.  

---

### **Step 5: Link Your Local Ollama to the Public Ngrok URL**  

1. Copy the **Ngrok URL** from the notebook’s output.  
2. Open your **command-line terminal** (Mac Terminal, Command Prompt, or PowerShell).  
3. Run the following command, replacing `<paste_url_here>` with your Ngrok URL:  

   ```bash
   export OLLAMA_HOST=<paste_url_here>
   ```

4. If using a **static Ngrok URL**, save this command for future sessions.  

---

### **Step 6: Run Ollama**  

1. Verify Ollama is running by listing available models:  

   ```bash
   ollama list
   ```

2. If no models are found, download one (e.g., **LLaMA 3**):  

   ```bash
   ollama run llama3
   ```

3. You can now interact with Ollama in real-time, leveraging **Google Colab’s computing power**.  

---

## **🔄 Restarting or Stopping Ollama on Colab**  

- To **stop Ollama**, disconnect from Google Colab and delete the runtime.  
- To **restart Ollama**, follow these steps:  
  1. **Run the Jupyter notebook** ([Step 4](#step-4-run-the-jupyter-notebook)).  
  2. **Reconfigure the Ollama host** ([Step 5](#step-5-link-your-local-ollama-to-the-public-ngrok-url)).  

---

## **💾 Alternative: Save Ollama Models to Google Drive**  

- If you want to **store models on Google Drive**, you can modify the setup to load models from your drive.  
- Note: Running Ollama models from Google Drive may be **slower** and could cause **connectivity issues** with Ngrok.  

