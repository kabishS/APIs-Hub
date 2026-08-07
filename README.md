# 🌐 Free APIs for Developers & Students

A curated collection of **free public APIs** for developers, students, hackathons, and learning projects. All APIs listed here are free to use (or have a free tier) and can help you build applications faster.

## 📑 Table of Contents

- [Job APIs](#job-apis)
- [AI APIs](#ai-apis)
- [Education APIs](#education-apis)
- [Weather APIs](#weather-apis)
- [Utility APIs](#utility-apis)
- [Contributing](#contributing)
- [License](#license)

---

## 💼 Job APIs

| API Name | Description | API |
|----------|-------------|-----|
| [Himalayas](https://himalayas.app/api) | Remote job board and search engine | https://himalayas.app/jobs/api |
| [Jobicy](https://jobicy.com/jobs-rss-feed) | Remote job listings API | https://jobicy.com/api/v2/remote-jobs |
| [Adzuna](https://developer.adzuna.com/) | Job search API | https://api.adzuna.com/v1/api/jobs |

---

## 🤖 AI APIs

| API Name | Description | API |
|----------|-------------|-----|
| [OpenRouter](https://openrouter.ai/) | Access multiple AI models through one API | https://openrouter.ai/api/v1 |
| [Hugging Face](https://huggingface.co/docs/api-inference/index) | AI inference API | https://api-inference.huggingface.co |
| [Gemini API](https://ai.google.dev/) | Google's Generative AI API | https://generativelanguage.googleapis.com |

---

## 🎓 Education APIs

| API Name | Description | API |
|----------|-------------|-----|
| [Open Trivia DB](https://opentdb.com/) | Trivia and quiz questions | https://opentdb.com/api.php |
| [Dictionary API](https://dictionaryapi.dev/) | Free English dictionary | https://api.dictionaryapi.dev/api/v2/entries/en |
| [University Domains](https://github.com/Hipo/university-domains-list) | Universities worldwide | http://universities.hipolabs.com/search |

---

## 🌤️ Weather APIs

| API Name | Description | API |
|----------|-------------|-----|
| [Open-Meteo](https://open-meteo.com/) | Free weather forecast API | https://api.open-meteo.com/v1/forecast |
| [WeatherAPI](https://www.weatherapi.com/) | Weather and forecast data | https://api.weatherapi.com/v1 |

---

## 🛠️ Utility APIs

| API Name | Description | API |
|----------|-------------|-----|
| [REST Countries](https://restcountries.com/) | Country information | https://restcountries.com/v3.1/all |
| [JSONPlaceholder](https://jsonplaceholder.typicode.com/) | Fake REST API for testing | https://jsonplaceholder.typicode.com |
| [ReqRes](https://reqres.in/) | Fake API for frontend testing | https://reqres.in/api |

---

## 🚀 Example Usage

### JavaScript (Fetch)

```javascript
fetch("https://himalayas.app/jobs/api")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

### Python

```python
import requests

response = requests.get("https://himalayas.app/jobs/api")
print(response.json())
```

### cURL

```bash
curl https://himalayas.app/jobs/api
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork this repository.
2. Add your API to the appropriate table.
3. Open a Pull Request.

---

## 📄 License

This project is licensed under the **MIT License**.

---

⭐ If you find this repository useful, consider giving it a **star** on GitHub!
