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
