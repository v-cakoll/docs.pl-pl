---
title: „<attribute>" nie może być zastosowane, ponieważ format identyfikatora GUID „<number>" jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: f7b6e42480075666ce9f7e8fc6966bd4bb6b888a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977313"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>nie można zastosować elementu "\<Attribute >", ponieważ format identyfikatora GUID "\<Number >" jest niepoprawny

Blok atrybutów `COMClassAttribute` określa unikatowy identyfikator globalny (GUID), który jest niezgodny z właściwym formatem identyfikatora GUID. `COMClassAttribute` używa identyfikatorów GUID do unikatowego identyfikowania klasy, interfejsu i zdarzenia utworzenia.  
  
 Identyfikator GUID składa się z 16 bajtów, z których pierwsze osiem jest liczbowe, a ostatnie osiem są binarne. Jest on generowany przez narzędzia firmy Microsoft, takie jak uuidgen. exe, i gwarantuje, że jest to unikatowe miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do zidentyfikowania obiektu COM.  
  
2. Upewnij się, że ciągi identyfikatorów GUID przedstawiane w bloku atrybutów `COMClassAttribute` są poprawnie kopiowane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Guid>
- [Przegląd atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md)
