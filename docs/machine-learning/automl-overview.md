---
title: Automatyczne usługi machine learning za pomocą platformy ML.NET
description: Omówienie modelu automatycznego wyboru i szkolenia
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 39e454d67f60280c6a43e3b80d788d873345ab77
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307386"
---
# <a name="automated-machine-learning-with-mlnet"></a>Automatyczne usługi machine learning za pomocą platformy ML.NET

Automatyczne machine learning to funkcja strukturze ML.NET wykonujący wybór modelu automatyczne i szkolenia. Określić zadanie machine learning i podać zestaw danych i automatyczne ML wybiera model zawierający najważniejsze metryki. Dane wyjściowe:
- Plik modelu, które mogą być ładowane do aplikacji prognoz
- Kod aplikacji w celu prognozowania
- Kod źródłowy, umożliwiający wybór funkcji i model, szkolenie (informacje o modelu)

> [!NOTE]
> Ta funkcja jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. 

Automatyczne ML jest obecnie ograniczona do uczenia maszynowego [zadania](resources/tasks.md) klasyfikacji binarnej, wieloklasowej klasyfikacji i regresji. Inne usługi machine learning zadania będą obsługiwane w przyszłych wydaniach.

Istnieją trzy sposoby na wykorzystanie ML automatyczne:
1. W wierszu polecenia za pomocą [interfejsu wiersza polecenia w strukturze ML.NET](automate-training-with-cli.md)
1. Za pomocą aplikacji za pomocą [automatyczne interfejsu API uczenia Maszynowego](how-to-guides/how-to-use-the-automl-api.md)
1. Za pomocą graficznego interfejsu użytkownika, za pomocą konstruktora modelu strukturze ML.NET
