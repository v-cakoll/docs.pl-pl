---
title: Przewodnik po strukturze ML.NET zawartości
description: Dowiedz się, jak tworzyć niestandardowych rozwiązań sztucznej Inteligencji i integrowanie aplikacji .NET za pomocą strukturze ML.NET
ms.date: 01/18/2019
ms.custom: seodec18
ms.openlocfilehash: d80ba8ec2d563960242765f1ffbedec3e8882954
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550464"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="9df6f-103">Przewodnik po strukturze ML.NET zawartości</span><span class="sxs-lookup"><span data-stu-id="9df6f-103">ML.NET Content Guide</span></span>

<span data-ttu-id="9df6f-104">Ten przewodnik wyjaśnia podstawowe pojęcia i zawiera samouczki i dokumentacja interfejsu API do pracy za pomocą platformy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9df6f-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="9df6f-105">Ta dokumentacja dotyczy strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="9df6f-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="9df6f-106">Materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9df6f-106">Material may be subject to change.</span></span> <span data-ttu-id="9df6f-107">Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9df6f-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="9df6f-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="9df6f-108">Get started</span></span>

<span data-ttu-id="9df6f-109">Aby zainstalować i zacznij tworzyć w strukturze ML.NET, postępuj zgodnie z [samouczek z wprowadzeniem](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span><span class="sxs-lookup"><span data-stu-id="9df6f-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="9df6f-110">Aby dowiedzieć się więcej o strukturze ML.NET, zobacz [co to jest strukturze ML.NET?](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="9df6f-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="9df6f-111">Aby poznać podstawy, zobacz [podstawowe pojęcia do trenowania modelu w strukturze ML.NET](basic-concepts-model-training-in-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="9df6f-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="9df6f-112">Samouczki</span><span class="sxs-lookup"><span data-stu-id="9df6f-112">Tutorials</span></span>

<span data-ttu-id="9df6f-113">[Analizowanie opinii za pomocą model klasyfikacji binarnej](tutorials/sentiment-analysis.md) pokazuje, jak utworzyć aplikację, która określa, czy Tonacja jest dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="9df6f-113">[Analyze sentiment using a binary classification model](tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="9df6f-114">[Klasyfikowanie problemów w usłudze GitHub za pomocą modelu klasyfikacji wieloklasowej](tutorials/github-issue-classification.md) pokazuje, jak utworzyć aplikację, która określa etykietę obszar problemu w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="9df6f-114">[Classify GitHub issues using a multiclass classification model](tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="9df6f-115">[Przewidywanie taryfy taksówek za pomocą modelu regresji](tutorials/taxi-fare.md) przedstawiono sposób tworzenia predykcyjnego aplikację, która używa wielu czynników z danych historycznych w celu ustalenia odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="9df6f-115">[Predict taxi fare using a regression model](tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="9df6f-116">[Klasyfikowanie irysów kwiatów przy użyciu funkcji](tutorials/iris-clustering.md) pokazano, jak model klastrowania umożliwia analizowanie zestawu danych iris.</span><span class="sxs-lookup"><span data-stu-id="9df6f-116">[Classify iris flowers by features](tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span> 

## <a name="how-to-guide"></a><span data-ttu-id="9df6f-117">Jak przewodnik</span><span class="sxs-lookup"><span data-stu-id="9df6f-117">How to guide</span></span>

<span data-ttu-id="9df6f-118">[Tworzenie aplikacji gry dopasowania w górę listy Infer.NET i programowania Probabilistyczne](how-to-guides/matchup-app-infer-net.md) dowiesz się, jak tworzyć uproszczoną wersję aplikacji dopasowania w górę, jak powinny zostać wyświetlone gier Xbox.</span><span class="sxs-lookup"><span data-stu-id="9df6f-118">[Build a game match-up list app with Infer.NET and probabilistic programming](how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="9df6f-119">Resources</span><span class="sxs-lookup"><span data-stu-id="9df6f-119">Resources</span></span>

<span data-ttu-id="9df6f-120">[Machine learning słownik](resources/glossary.md) definiuje terminologii.</span><span class="sxs-lookup"><span data-stu-id="9df6f-120">[Machine learning glossary](resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="9df6f-121">[Zadania uczenia maszynowego](resources/tasks.md) w tym artykule opisano zadania, takie jak Klasyfikacja i wykrywanie anomalii.</span><span class="sxs-lookup"><span data-stu-id="9df6f-121">[Machine learning tasks](resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="9df6f-122">[Przekształcenia danych](resources/transforms.md) zawiera opis możliwości przygotowywania danych w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9df6f-122">[Data transforms](resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>


## <a name="api-reference"></a><span data-ttu-id="9df6f-123">Odwołanie API</span><span class="sxs-lookup"><span data-stu-id="9df6f-123">API reference</span></span>

<span data-ttu-id="9df6f-124">[Dokumentacja interfejsu API w strukturze ML.NET](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) opisuje szerokość interfejsami API dostępnymi.</span><span class="sxs-lookup"><span data-stu-id="9df6f-124">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
