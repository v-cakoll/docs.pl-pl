---
title: Automatyczne Uczenie maszynowe za pomocą ML.NET
description: Przegląd automatycznego wyboru modelu i szkolenia
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 251ca50f062f415ac4dfeda243eb746e9744b6f4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345188"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="2296f-103">Automatyczne Uczenie maszynowe za pomocą ML.NET</span><span class="sxs-lookup"><span data-stu-id="2296f-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="2296f-104">Automatyczne Uczenie maszynowe to funkcja ML.NET, która wykonuje automatyczne wybieranie modelu i szkolenie.</span><span class="sxs-lookup"><span data-stu-id="2296f-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="2296f-105">Należy określić zadanie uczenia maszynowego i dostarczyć zestaw danych, a zautomatyzowanej ML wybiera model z najlepszymi metrykami.</span><span class="sxs-lookup"><span data-stu-id="2296f-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="2296f-106">Dane wyjściowe IT:</span><span class="sxs-lookup"><span data-stu-id="2296f-106">It outputs:</span></span>

- <span data-ttu-id="2296f-107">plik modelu, który można załadować do aplikacji predykcyjnej</span><span class="sxs-lookup"><span data-stu-id="2296f-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="2296f-108">kod aplikacji do prognozowania</span><span class="sxs-lookup"><span data-stu-id="2296f-108">application code to make predictions</span></span>
- <span data-ttu-id="2296f-109">kod źródłowy używany do wyboru funkcji i szkolenia modelu (aby zrozumieć model)</span><span class="sxs-lookup"><span data-stu-id="2296f-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="2296f-110">Ta funkcja jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie materiał.</span><span class="sxs-lookup"><span data-stu-id="2296f-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="2296f-111">Automatyczna ML jest obecnie ograniczona do [zadań](resources/tasks.md) uczenia maszynowego klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji.</span><span class="sxs-lookup"><span data-stu-id="2296f-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="2296f-112">Inne zadania uczenia maszynowego będą obsługiwane w przyszłych wydaniach.</span><span class="sxs-lookup"><span data-stu-id="2296f-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="2296f-113">Istnieją trzy sposoby używania zautomatyzowanej ML:</span><span class="sxs-lookup"><span data-stu-id="2296f-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="2296f-114">Przy użyciu graficznego interfejsu użytkownika z [konstruktorem modelu ml.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="2296f-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="2296f-115">W wierszu polecenia, z [interfejsem CLI ml.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="2296f-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="2296f-116">Za pośrednictwem aplikacji, za pomocą [interfejsu API zautomatyzowanej](how-to-guides/how-to-use-the-automl-api.md) tablicy</span><span class="sxs-lookup"><span data-stu-id="2296f-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
