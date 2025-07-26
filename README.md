# Vertex AI Prompt Optimizer: Conference Talk & Demo Repository

[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-Vertex%20AI-4285F4?style=flat-square&logo=googlecloud)](https://cloud.google.com/vertex-ai)
[![Conference Talk](https://img.shields.io/badge/Conference-Talk%20Materials-FF6B6B?style=flat-square)](https://github.com)

**Conference Repository**: Materials and demos for a talk on Google Cloud's Vertex AI Prompt Optimizer - systematic prompt engineering with mathematical evaluation for production AI applications.

## Overview

This presentation demonstrates how to leverage **Vertex AI Prompt Optimizer** to:
- Systematically optimize prompts instead of manual trial-and-error
- Mathematically evaluate prompt performance using quantitative metrics
- Migrate prompts across different LLMs (GPT-4 → Gemini, etc.)
- Scale prompt engineering across teams and use cases
- Deliver measurably better AI products to customers

## What is Vertex AI Prompt Optimizer?

Vertex AI Prompt Optimizer uses **iterative LLM-based optimization algorithms** to automatically find optimal prompts for any target model. Instead of manual engineering:

**Traditional Process**: Trial & Error → Inconsistent Results → Wasted Time  
**Automated Process**: Labeled Examples → Mathematical Optimization → Optimal Prompts

### How It Works
1. **Input**: Labeled training examples (input-output pairs)
2. **Optimization**: Algorithm iteratively generates and evaluates candidate prompts
3. **Evaluation**: Mathematical metrics determine best performing prompts
4. **Output**: Optimized instructions and demonstrations for your target model

Based on Google Research's [Automatic Prompt Optimization (APO) methods](https://arxiv.org/abs/2406.15708) accepted by NeurIPS 2024.

## Repository Structure

```
google-io/
├── README.md                     # This guide
├── prompt_template.txt           # Base prompt template
├── sample_marketing.jsonl        # Full marketing dataset
├── sample_marketing_good.jsonl   # High-quality examples
├── sample_marketing_minimal.jsonl # Minimal viable dataset
├── pdf.md                       # Research summary & use cases
└── 2406.15708v2.pdf            # Original research paper
```

## Demo Use Case: Marketing Copy Optimization

**Challenge**: Generate consistent, high-converting marketing copy across campaigns

**Dataset**: The `sample_marketing_*.jsonl` files contain real-world examples:
- B2B SaaS email subject lines
- Social media ad copy
- Product descriptions
- SEO content

**Example Training Data**:
```json
{
  "question": "Write email subject line for B2B SaaS free trial conversion",
  "article": "Product: ExpenseAI. Trial conversion rate: 12% (need 25%). CFO pain points: manual expense reports...",
  "target": "{FirstName}, your team loses $12,400/month on expense reports"
}
```

## Quick Start

### Prerequisites
- Google Cloud Project with Vertex AI enabled
- Python 3.8+ with Vertex AI SDK
- Access to Vertex AI Prompt Optimizer (Public Preview)

### Basic Implementation
```python
from google.cloud import aiplatform

# Configure optimization
params = {
    'num_steps': 10,
    'target_model': 'gemini-1.5-flash',
    'eval_metrics_types': ['question_answering_quality'],
    'optimization_mode': 'instruction_and_demo',
    'input_data_path': 'gs://your-bucket/training-data.jsonl',
    'output_data_path': 'gs://your-bucket/optimized-prompts/'
}

# Run optimization job
custom_job = aiplatform.CustomJob(
    display_name="prompt-optimization-job",
    worker_pool_specs=WORKER_POOL_SPECS,
)
custom_job.run()
```

## Evaluation Metrics

**Built-in Metrics**:
- Question Answering Quality
- Groundedness
- BLEU/ROUGE Scores
- Fluency

**Performance Improvements** typically seen:
- 30-50% better task completion rates
- 25% improvement in user satisfaction scores
- 40% reduction in prompt engineering time

## Take-Home Assignment: Optimize & Contribute

**Challenge**: Create optimized prompts that rank high on our evaluation metrics and contribute them to this repository.

### Your Mission
1. **Choose a use case** from the marketing examples or create your own
2. **Use Vertex AI Prompt Optimizer** to generate optimized prompts
3. **Test your prompts** against the evaluation metrics
4. **Submit a Pull Request** with your optimized prompt and results

### Contribution Format
Create a new file: `contributions/your-name-prompt-optimization.json`

```json
{
  "contributor": "Your Name",
  "use_case": "Description of your optimization target",
  "original_prompt": "Your starting prompt",
  "optimized_prompt": "Your optimized prompt from Vertex AI",
  "evaluation_metrics": {
    "question_answering_quality": 4.2,
    "groundedness": 3.8,
    "custom_metric": 4.5
  },
  "improvement_percentage": "25% improvement over baseline",
  "notes": "Key insights from your optimization process"
}
```

### Evaluation Criteria
- **Performance Improvement**: Higher scores on evaluation metrics
- **Use Case Relevance**: Real-world applicability
- **Documentation Quality**: Clear explanation of optimization process
- **Innovation**: Creative application of the optimizer

### Recognition
- Best contributions will be featured in follow-up presentations
- Contributors will be acknowledged in conference materials
- Top optimizations may be included in production case studies

**Deadline**: Submit PRs within 30 days of the conference

## Conference Talk Key Points

**"From Manual Prompting to Mathematical Optimization"**

1. **Stop guessing** - Use mathematical optimization instead of trial-and-error
2. **Scale systematically** - Optimize prompts across teams and use cases  
3. **Measure everything** - Quantify prompt performance with metrics
4. **Future-proof your AI** - Easily migrate prompts between models

## Resources

### Official Documentation
- [Vertex AI Prompt Optimizer Overview](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/prompts/prompt-optimizer)
- [Google Developers Blog Post](https://developers.googleblog.com/en/enhance-your-prompts-with-vertex-ai-prompt-optimizer/)

### Research Foundation
- **Paper**: "Automatic Prompt Optimization" (NeurIPS 2024)
- **File**: `2406.15708v2.pdf` in this repository

### Code Examples
- [GitHub: Vertex AI Prompt Optimizer SDK](https://github.com/GoogleCloudPlatform/vertex-ai-samples/tree/main/notebooks/official/prompt_optimizer)

## Business Impact

Organizations report:
- Faster time-to-market for AI features
- Consistent quality across all AI outputs  
- Reduced engineering overhead for prompt maintenance
- Better ROI on AI investments through measurable improvements

## Contributing

**For Take-Home Assignment**: Follow the guidelines above and submit PRs
**For Conference Questions**: Contact the speaker
**For Technical Issues**: [Google Cloud Support](https://cloud.google.com/support)

---

**Ready to optimize?** Start with the examples in this repository and visit the [Vertex AI Console](https://console.cloud.google.com/vertex-ai) to begin.