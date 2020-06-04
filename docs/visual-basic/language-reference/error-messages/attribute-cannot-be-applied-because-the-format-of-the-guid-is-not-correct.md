---
title: „<attribute>" nie może być zastosowane, ponieważ format identyfikatora GUID „<number>" jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 554c38c8f44999feba4cfa04d58ce2f07e955eb1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409923"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>„\<attribute>" nie może być zastosowane, ponieważ format identyfikatora GUID „\<number>" jest nieprawidłowy

`COMClassAttribute`Blok atrybutu określa unikatowy identyfikator globalny (GUID), który jest niezgodny z właściwym formatem identyfikatora GUID. `COMClassAttribute`używa identyfikatorów GUID do unikatowego identyfikowania klasy, interfejsu i zdarzenia utworzenia.  
  
 Identyfikator GUID składa się z 16 bajtów, z których pierwsze osiem jest liczbowe, a ostatnie osiem są binarne. Jest on generowany przez narzędzia firmy Microsoft, takie jak uuidgen. exe, i gwarantuje, że jest to unikatowe miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do zidentyfikowania obiektu COM.  
  
2. Upewnij się, że ciągi identyfikatorów GUID przedstawiane w `COMClassAttribute` bloku atrybutu zostały skopiowane poprawnie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Guid>
- [Przegląd atrybutów](../../programming-guide/concepts/attributes/index.md)
