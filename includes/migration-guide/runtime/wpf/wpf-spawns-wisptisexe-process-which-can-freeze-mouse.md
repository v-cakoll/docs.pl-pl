---
ms.openlocfilehash: cbd599f7467c3b360bbe1c76a65abfdb840a1530
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118758"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF spowoduje utworzenie proces wisptis.exe, który można zablokować myszy

|   |   |
|---|---|
|Szczegóły|Problem został wprowadzony w wersji 4.5.2, który powoduje, że <code>wisptis.exe</code> do jest zduplikowany, można zablokować wprowadzanie za pomocą myszy.|
|Sugestia|Poprawkę rozwiązującą ten problem jest dostępna w wersji obsługi programu .NET Framework 4.5.2 (pakiet zbiorczy poprawek 3026376) lub po uaktualnieniu do programu .NET Framework 4.6|
|Zakres|Duży|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
