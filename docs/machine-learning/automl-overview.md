---
title: Zautomatyzowane uczenie maszynowe z ML.NET
description: Przegląd automatycznego doboru modeli i szkoleń
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: acd6cae71d2d5d79209a77d34175e7f1b3c1ee35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849357"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="6cf01-103">Zautomatyzowane uczenie maszynowe z ML.NET</span><span class="sxs-lookup"><span data-stu-id="6cf01-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="6cf01-104">Zautomatyzowane uczenie maszynowe jest funkcją ML.NET, która wykonuje automatyczny wybór modelu i szkolenia.</span><span class="sxs-lookup"><span data-stu-id="6cf01-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="6cf01-105">Określ zadanie uczenia maszynowego i podać zestaw danych, a zautomatyzowany program ML wybiera model z najlepszymi metrykami.</span><span class="sxs-lookup"><span data-stu-id="6cf01-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="6cf01-106">Wyprowadza:</span><span class="sxs-lookup"><span data-stu-id="6cf01-106">It outputs:</span></span>

- <span data-ttu-id="6cf01-107">plik modelu, który można załadować do aplikacji przewidywania</span><span class="sxs-lookup"><span data-stu-id="6cf01-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="6cf01-108">kod aplikacji do przewidywania</span><span class="sxs-lookup"><span data-stu-id="6cf01-108">application code to make predictions</span></span>
- <span data-ttu-id="6cf01-109">kod źródłowy używany do wyboru funkcji i szkolenia modelu (aby zrozumieć model)</span><span class="sxs-lookup"><span data-stu-id="6cf01-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="6cf01-110">Ta funkcja jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="6cf01-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="6cf01-111">Automatyczny ml jest obecnie ograniczona do [zadań](resources/tasks.md) uczenia maszynowego klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji.</span><span class="sxs-lookup"><span data-stu-id="6cf01-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="6cf01-112">Inne zadania uczenia maszynowego będą obsługiwane w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="6cf01-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="6cf01-113">Istnieją trzy sposoby korzystania z automatycznego ml:</span><span class="sxs-lookup"><span data-stu-id="6cf01-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="6cf01-114">Z graficznym interfejsem użytkownika z [ML.NET Model Builder](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="6cf01-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="6cf01-115">W wierszu polecenia z [ML.NET CLI](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="6cf01-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="6cf01-116">Za pośrednictwem aplikacji, z [automatycznym ML API](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="6cf01-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
