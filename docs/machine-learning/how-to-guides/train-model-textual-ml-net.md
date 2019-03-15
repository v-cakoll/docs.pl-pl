---
title: Zastosuj technicznego opracowywania funkcji do trenowania modelu danych tekstowych — strukturze ML.NET
description: Dowiedz się, jak można zastosować technicznego opracowywania funkcji do trenowania modelu danych tekstowych za pomocą platformy ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: e26a4b293869b7cdad3c439237bd0145cafa314a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57844360"
---
# <a name="apply-feature-engineering-for-machine-learning-model-training-on-textual-data-with-mlnet"></a><span data-ttu-id="70f99-103">Zastosuj technicznego opracowywania funkcji Machine learning model szkoleń dotyczących danych tekstowych za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="70f99-103">Apply feature engineering for machine learning model training on textual data with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="70f99-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="70f99-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="70f99-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="70f99-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="70f99-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="70f99-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="70f99-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="70f99-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="70f99-108">Należy przekonwertować żadnych danych innych niż float do `float` typy danych, ponieważ wszystkie strukturze ML.NET `learners` oczekiwane funkcje jak `float vector`.</span><span class="sxs-lookup"><span data-stu-id="70f99-108">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="70f99-109">Aby dowiedzieć się więcej na dane tekstowe, należy wyodrębnić funkcje tekstu.</span><span class="sxs-lookup"><span data-stu-id="70f99-109">To learn on textual data, you need to extract text features.</span></span> <span data-ttu-id="70f99-110">Strukturze ML.NET ma pewne podstawowe tekstu funkcję wyodrębniania mechanizmów:</span><span class="sxs-lookup"><span data-stu-id="70f99-110">ML.NET has some basic text feature extraction mechanisms:</span></span>

- <span data-ttu-id="70f99-111">`Text normalization` (usuwania znak interpunkcyjny, znaki diakrytyczne, przełączenie na małe litery itp.)</span><span class="sxs-lookup"><span data-stu-id="70f99-111">`Text normalization` (removing punctuation, diacritics, switching to lowercase etc.)</span></span>
- <span data-ttu-id="70f99-112">`Separator-based tokenization`.</span><span class="sxs-lookup"><span data-stu-id="70f99-112">`Separator-based tokenization`.</span></span>
- <span data-ttu-id="70f99-113">`Stopword` usuwanie.</span><span class="sxs-lookup"><span data-stu-id="70f99-113">`Stopword` removal.</span></span>
- <span data-ttu-id="70f99-114">`Ngram` i `skip-gram` wyodrębniania.</span><span class="sxs-lookup"><span data-stu-id="70f99-114">`Ngram` and `skip-gram` extraction.</span></span>
- <span data-ttu-id="70f99-115">`TF-IDF` Podczas ponownego skalowania.</span><span class="sxs-lookup"><span data-stu-id="70f99-115">`TF-IDF` rescaling.</span></span>
- <span data-ttu-id="70f99-116">`Bag of words` Konwersja.</span><span class="sxs-lookup"><span data-stu-id="70f99-116">`Bag of words` conversion.</span></span>

<span data-ttu-id="70f99-117">W poniższym przykładzie pokazano strukturze ML.NET tekst funkcję wyodrębniania mechanizmów przy użyciu [Wikipedia detox dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):</span><span class="sxs-lookup"><span data-stu-id="70f99-117">The following example demonstrates ML.NET text feature extraction mechanisms using the [Wikipedia detox dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):</span></span>

<!-- markdownlint-disable MD010 -->
```console
Sentiment   SentimentText
1   Stop trolling, zapatancas, calling me a liar merely demonstartes that you arer Zapatancas. You may choose to chase every legitimate editor from this site and ignore me but I am an editor with a record that isnt 99% trolling and therefore my wishes are not to be completely ignored by a sockpuppet like yourself. The consensus is overwhelmingly against you and your trolling lover Zapatancas,  
1   ::::: Why are you threatening me? I'm not being disruptive, its you who is being disruptive.   
0   " *::Your POV and propaganda pushing is dully noted. However listing interesting facts in a netral and unacusitory tone is not POV. You seem to be confusing Censorship with POV monitoring. I see nothing POV expressed in the listing of intersting facts. If you want to contribute more facts or edit wording of the cited fact to make them sound more netral then go ahead. No need to CENSOR interesting factual information. "
0   ::::::::This is a gross exaggeration. Nobody is setting a kangaroo court. There was a simple addition concerning the airline. It is the only one disputed here.   
```
<!-- markdownlint-enable MD010 -->

```csharp
// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("IsToxic", DataKind.BL, 0),
        new TextLoader.Column("Message", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the message texts that are read from the file.
var messageTexts = data.GetColumn<string>(mlContext, "Message").Take(20).ToArray();

// Apply various kinds of text operations supported by ML.NET.
var pipeline =
    // One-stop shop to run the full text featurization.
    mlContext.Transforms.Text.FeaturizeText("TextFeatures", "Message")

    // Normalize the message for later transforms
    .Append(mlContext.Transforms.Text.NormalizeText("NormalizedMessage", "Message"))

    // NLP pipeline 1: bag of words.
    .Append(new WordBagEstimator(mlContext, "BagOfWords", "NormalizedMessage"))

    // NLP pipeline 2: bag of bigrams, using hashes instead of dictionary indices.
    .Append(new WordHashBagEstimator(mlContext, "BagOfBigrams","NormalizedMessage", 
                ngramLength: 2, allLengths: false))

    // NLP pipeline 3: bag of tri-character sequences with TF-IDF weighting.
    .Append(mlContext.Transforms.Text.TokenizeCharacters("MessageChars", "Message"))
    .Append(new NgramExtractingEstimator(mlContext, "BagOfTrichar", "MessageChars", 
                ngramLength: 3, weighting: NgramExtractingEstimator.WeightingCriteria.TfIdf))

    // NLP pipeline 4: word embeddings.
    .Append(mlContext.Transforms.Text.TokenizeWords("TokenizedMessage", "NormalizedMessage"))
    .Append(mlContext.Transforms.Text.ExtractWordEmbeddings("Embeddings", "TokenizedMessage",
                WordEmbeddingsExtractingTransformer.PretrainedModelKind.GloVeTwitter25D));

// Let's train our pipeline, and then apply it to the same data.
// Note that even on a small dataset of 70KB the pipeline above can take up to a minute to completely train.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var embeddings = transformedData.GetColumn<float[]>(mlContext, "Embeddings").Take(10).ToArray();
var unigrams = transformedData.GetColumn<float[]>(mlContext, "BagOfWords").Take(10).ToArray();
```
