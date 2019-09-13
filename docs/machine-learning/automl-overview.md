---
title: Automatyczne Uczenie maszynowe za pomocą ML.NET
description: Przegląd automatycznego wyboru modelu i szkolenia
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: da2d764e678debc78a25faeb8e48facb44fc4021
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929423"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="6e8ea-103">Automatyczne Uczenie maszynowe za pomocą ML.NET</span><span class="sxs-lookup"><span data-stu-id="6e8ea-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="6e8ea-104">Automatyczne Uczenie maszynowe to funkcja ML.NET, która wykonuje automatyczne wybieranie modelu i szkolenie.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="6e8ea-105">Należy określić zadanie uczenia maszynowego i dostarczyć zestaw danych, a zautomatyzowanej ML wybiera model z najlepszymi metrykami.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="6e8ea-106">Dane wyjściowe IT:</span><span class="sxs-lookup"><span data-stu-id="6e8ea-106">It outputs:</span></span>

- <span data-ttu-id="6e8ea-107">plik modelu, który można załadować do aplikacji predykcyjnej</span><span class="sxs-lookup"><span data-stu-id="6e8ea-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="6e8ea-108">kod aplikacji do prognozowania</span><span class="sxs-lookup"><span data-stu-id="6e8ea-108">application code to make predictions</span></span>
- <span data-ttu-id="6e8ea-109">kod źródłowy używany do wyboru funkcji i szkolenia modelu (aby zrozumieć model)</span><span class="sxs-lookup"><span data-stu-id="6e8ea-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="6e8ea-110">Ta funkcja jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie materiał.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="6e8ea-111">Automatyczna ML jest obecnie ograniczona do [zadań](resources/tasks.md) uczenia maszynowego klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="6e8ea-112">Inne zadania uczenia maszynowego będą obsługiwane w przyszłych wydaniach.</span><span class="sxs-lookup"><span data-stu-id="6e8ea-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="6e8ea-113">Istnieją trzy sposoby używania zautomatyzowanej ML:</span><span class="sxs-lookup"><span data-stu-id="6e8ea-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="6e8ea-114">Przy użyciu graficznego interfejsu użytkownika z [konstruktorem modelu ml.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="6e8ea-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="6e8ea-115">W wierszu polecenia, z [interfejsem CLI ml.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="6e8ea-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="6e8ea-116">Za pośrednictwem aplikacji, za pomocą [interfejsu API zautomatyzowanej](how-to-guides/how-to-use-the-automl-api.md) tablicy</span><span class="sxs-lookup"><span data-stu-id="6e8ea-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
