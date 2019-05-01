---
title: Okres wykrywania wystąpień możliwych do uruchomienia
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 9652dd811f64e5324219b8aa0700ab8219edeeb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937959"
---
# <a name="runnable-instances-detection-period"></a>Okres wykrywania wystąpień możliwych do uruchomienia
Store wystąpienia przepływu pracy SQL uruchamia zadania wewnętrzne, okresowo budzi się i wykrywa możliwy do uruchomienia lub aktywowalnej wystąpień w bazie danych trwałości. **Możliwy do uruchomienia okres wykrywania wystąpień** właściwość Store wystąpienia przepływu pracy SQL określa okres czasu, po upływie którego Store wystąpienia przepływu pracy SQL uruchamia zadanie wykrywania, aby wykrywać wszelkie możliwe do uruchomienia lub aktywowalnej przepływu pracy wystąpień w bazie danych trwałości od poprzedniego cyklu wykrywania.  
  
 Ustawienie krótszy okres dla tej właściwości skraca czas między wygaśnięcia czasomierz skojarzonych z wystąpieniem przepływu pracy i sygnalizowanie zdarzenia oraz ładowanie kolejne wystąpienia. Jednak również zwiększa obciążenie przetwarzania na hoście i nie może być pożądane w scenariuszach, w którym występują rzadko trwałe czasomierze i/lub błędy hosta. Typ właściwości jest przedział czasu, a wartość właściwości w formacie:: mm: ss. Minimalna wartość tej właściwości to 00:00:01. Wartość domyślna właściwości to 00:00:05.  
  
 Aby uzyskać więcej informacji zobacz wykrywanie i aktywowanie wystąpienia przepływu pracy możliwy do uruchomienia i aktywowalnej [Aktywacja wystąpienia](instance-activation.md).
