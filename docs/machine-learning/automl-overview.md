---
title: Automatyczne Uczenie maszynowe za pomocą ML.NET
description: Przegląd automatycznego wyboru modelu i szkolenia
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 263004e67bf88af4182788e8c74cb410460e9201
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971402"
---
# <a name="automated-machine-learning-with-mlnet"></a>Automatyczne Uczenie maszynowe za pomocą ML.NET

Automatyczne Uczenie maszynowe to funkcja ML.NET, która wykonuje automatyczne wybieranie modelu i szkolenie. Należy określić zadanie uczenia maszynowego i dostarczyć zestaw danych, a zautomatyzowanej ML wybiera model z najlepszymi metrykami. Dane wyjściowe IT:

- plik modelu, który można załadować do aplikacji predykcyjnej
- kod aplikacji do prognozowania
- kod źródłowy używany do wyboru funkcji i szkolenia modelu (aby zrozumieć model)

> [!NOTE]
> Ta funkcja jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie materiał.

Automatyczna ML jest obecnie ograniczona do [zadań](resources/tasks.md) uczenia maszynowego klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji. Inne zadania uczenia maszynowego będą obsługiwane w przyszłych wydaniach.

Istnieją trzy sposoby używania zautomatyzowanej ML:

1. Przy użyciu graficznego interfejsu użytkownika z [konstruktorem modelu ml.NET](automate-training-with-model-builder.md)
1. W wierszu polecenia, z [interfejsem CLI ml.NET](automate-training-with-cli.md)
1. Za pośrednictwem aplikacji, za pomocą [interfejsu API zautomatyzowanej](how-to-guides/how-to-use-the-automl-api.md) tablicy
