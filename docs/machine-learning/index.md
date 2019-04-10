---
title: Przewodnik po zawartości struktury ML.NET
description: Dowiedz się, jak tworzyć niestandardowe rozwiązania za pomocą sztucznej inteligencji i łączyć je z aplikacją .NET za pomocą struktury ML.NET
ms.date: 04/05/2019
ms.custom: seodec18
ms.openlocfilehash: de681daea5a29a121d350271ced4ccc2c0b1b533
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231334"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="c86ed-103">Przewodnik po zawartości struktury ML.NET</span><span class="sxs-lookup"><span data-stu-id="c86ed-103">ML.NET Content Guide</span></span>

<span data-ttu-id="c86ed-104">Ten przewodnik wyjaśnia podstawowe pojęcia oraz zawiera samouczki i dokumentację interfejsu API dla struktury ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c86ed-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="c86ed-105">Ta dokumentacja dotyczy struktury ML.NET, która jest obecnie dostępna w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="c86ed-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="c86ed-106">Materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="c86ed-106">Material may be subject to change.</span></span> <span data-ttu-id="c86ed-107">Aby uzyskać więcej informacji, zobacz [Wprowadzenie do struktury ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c86ed-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="c86ed-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c86ed-108">Get started</span></span>

<span data-ttu-id="c86ed-109">Aby zainstalować strukturę ML.NET i zacząć tworzyć za jej pomocą, skorzystaj z [samouczka z wprowadzeniem](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span><span class="sxs-lookup"><span data-stu-id="c86ed-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="c86ed-110">Aby dowiedzieć się więcej o strukturze ML.NET, zobacz [Co to jest struktura ML.NET?](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="c86ed-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="c86ed-111">Aby poznać podstawy, zobacz [Podstawowe pojęcia dotyczące trenowania modelu w strukturze ML.NET](basic-concepts-model-training-in-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="c86ed-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="c86ed-112">Samouczki</span><span class="sxs-lookup"><span data-stu-id="c86ed-112">Tutorials</span></span>

<span data-ttu-id="c86ed-113">[Analizowanie opinii za pomocą modelu klasyfikacji binarnej](./tutorials/sentiment-analysis.md) pokazuje, jak utworzyć aplikację, która określi, czy opinia jest pozytywna czy negatywna.</span><span class="sxs-lookup"><span data-stu-id="c86ed-113">[Analyze sentiment using a binary classification model](./tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="c86ed-114">[Klasyfikowanie problemów w usłudze GitHub za pomocą modelu klasyfikacji wieloklasowej](./tutorials/github-issue-classification.md) pokazuje, jak utworzyć aplikację, która określi etykietę obszaru problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="c86ed-114">[Classify GitHub issues using a multiclass classification model](./tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="c86ed-115">[Przewidywanie cen przy użyciu modelu regresji](./tutorials/taxi-fare.md) pokazuje, jak stworzyć aplikację, która przewiduje cenę przy użyciu wielu czynników z danych historycznych.</span><span class="sxs-lookup"><span data-stu-id="c86ed-115">[Predict prices using a regression model](./tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="c86ed-116">[Klasyfikowanie irysów według ich cech](./tutorials/iris-clustering.md) pokazuje w jaki sposób model klastrowania umożliwia analizowanie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="c86ed-116">[Classify iris flowers by features](./tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span>

<span data-ttu-id="c86ed-117">[Utwórz polecania filmów za pomocą platformy ML.NET](./tutorials/movie-recommmendation.md) dowiesz się, jak utworzyć aplikację zalecenie, aby zalecić filmy dla użytkowników na podstawie ich historii.</span><span class="sxs-lookup"><span data-stu-id="c86ed-117">[Create a Movie Recommender with ML.NET](./tutorials/movie-recommmendation.md) shows you how to build a recommendation app to recommend movies to users based on their history.</span></span>

<span data-ttu-id="c86ed-118">[Tworzenie klasyfikatora obrazu niestandardowego strukturze ML.NET z TensorFlow](./tutorials/image-classification.md): Pokazuje, jak ponowne szkolenie z istniejącego modelu Tensorflow do utworzenia przy użyciu strukturze ML.NET klasyfikatora obrazu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c86ed-118">[Build an ML.NET custom image classifier with TensorFlow](./tutorials/image-classification.md): demonstrates how to retrain an existing Tensorflow model to create a custom image classifier using ML.NET.</span></span>

## <a name="how-to-guide"></a><span data-ttu-id="c86ed-119">Przewodnik z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c86ed-119">How to guide</span></span>

<span data-ttu-id="c86ed-120">[Tworzenie aplikacji do dopasowywania graczy do jednej rozgrywki za pomocą Infer.NET i programowania probabilistycznego](./how-to-guides/matchup-app-infer-net.md) – poradnik ten pokazuje, jak stworzyć uproszczony system dopasowywania graczy do jednej rozgrywki, podobny do użytego w grach na konsolę Xbox.</span><span class="sxs-lookup"><span data-stu-id="c86ed-120">[Build a game match-up list app with Infer.NET and probabilistic programming](./how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="c86ed-121">Zasoby</span><span class="sxs-lookup"><span data-stu-id="c86ed-121">Resources</span></span>

<span data-ttu-id="c86ed-122">[Słownik pojęć na temat uczenia maszynowego](./resources/glossary.md) – znajdziesz tutaj wyjaśnienie kluczowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="c86ed-122">[Machine learning glossary](./resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="c86ed-123">[Zadania do wykonania za pomocą uczenia maszynowego](./resources/tasks.md) – w tym artykule opisano zadania, takie jak klasyfikowanie i wykrywanie anomalii.</span><span class="sxs-lookup"><span data-stu-id="c86ed-123">[Machine learning tasks](./resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="c86ed-124">[Przekształcenia danych](./resources/transforms.md) zawiera opis możliwości przygotowywania danych w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c86ed-124">[Data transforms](./resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>

## <a name="api-reference"></a><span data-ttu-id="c86ed-125">Dokumentacja interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c86ed-125">API reference</span></span>

<span data-ttu-id="c86ed-126">[Dokumentacja interfejsów API w strukturze ML.NET](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) opisuje pełen zakres dostępnych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="c86ed-126">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
