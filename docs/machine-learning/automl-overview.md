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
# <a name="automated-machine-learning-with-mlnet"></a>Zautomatyzowane uczenie maszynowe z ML.NET

Zautomatyzowane uczenie maszynowe jest funkcją ML.NET, która wykonuje automatyczny wybór modelu i szkolenia. Określ zadanie uczenia maszynowego i podać zestaw danych, a zautomatyzowany program ML wybiera model z najlepszymi metrykami. Wyprowadza:

- plik modelu, który można załadować do aplikacji przewidywania
- kod aplikacji do przewidywania
- kod źródłowy używany do wyboru funkcji i szkolenia modelu (aby zrozumieć model)

> [!NOTE]
> Ta funkcja jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.

Automatyczny ml jest obecnie ograniczona do [zadań](resources/tasks.md) uczenia maszynowego klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji. Inne zadania uczenia maszynowego będą obsługiwane w przyszłych wersjach.

Istnieją trzy sposoby korzystania z automatycznego ml:

1. Z graficznym interfejsem użytkownika z [ML.NET Model Builder](automate-training-with-model-builder.md)
1. W wierszu polecenia z [ML.NET CLI](automate-training-with-cli.md)
1. Za pośrednictwem aplikacji, z [automatycznym ML API](how-to-guides/how-to-use-the-automl-api.md)
