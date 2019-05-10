---
title: Automatyczne usługi machine learning za pomocą platformy ML.NET
description: Omówienie modelu automatycznego wyboru i szkolenia
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e6654718f174c9d8b628b05d85d74952c222eb66
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452735"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="9813b-103">Automatyczne usługi machine learning za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="9813b-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="9813b-104">Automatyczne machine learning to funkcja strukturze ML.NET wykonujący wybór modelu automatyczne i szkolenia.</span><span class="sxs-lookup"><span data-stu-id="9813b-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="9813b-105">Określić zadanie machine learning i podać zestaw danych i automatyczne ML wybiera model zawierający najważniejsze metryki.</span><span class="sxs-lookup"><span data-stu-id="9813b-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="9813b-106">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9813b-106">It outputs:</span></span>
- <span data-ttu-id="9813b-107">Plik modelu, które mogą być ładowane do aplikacji prognoz</span><span class="sxs-lookup"><span data-stu-id="9813b-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="9813b-108">Kod aplikacji w celu prognozowania</span><span class="sxs-lookup"><span data-stu-id="9813b-108">application code to make predictions</span></span>
- <span data-ttu-id="9813b-109">Kod źródłowy, umożliwiający wybór funkcji i model, szkolenie (informacje o modelu)</span><span class="sxs-lookup"><span data-stu-id="9813b-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="9813b-110">Ta funkcja jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9813b-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="9813b-111">Automatyczne ML jest obecnie ograniczona do uczenia maszynowego [zadania](resources/tasks.md) klasyfikacji binarnej, wieloklasowej klasyfikacji i regresji.</span><span class="sxs-lookup"><span data-stu-id="9813b-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="9813b-112">Inne usługi machine learning zadania będą obsługiwane w przyszłych wydaniach.</span><span class="sxs-lookup"><span data-stu-id="9813b-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="9813b-113">Istnieją trzy sposoby na wykorzystanie ML automatyczne:</span><span class="sxs-lookup"><span data-stu-id="9813b-113">There are three ways to use automated ML:</span></span>
1. <span data-ttu-id="9813b-114">W wierszu polecenia za pomocą [interfejsu wiersza polecenia w strukturze ML.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="9813b-114">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="9813b-115">Za pomocą aplikacji za pomocą [automatyczne interfejsu API uczenia Maszynowego](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="9813b-115">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
1. <span data-ttu-id="9813b-116">Za pomocą graficznego interfejsu użytkownika za pomocą konstruktora modeli strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="9813b-116">With a graphical user interface, with the the ML.NET Model Builder</span></span>
