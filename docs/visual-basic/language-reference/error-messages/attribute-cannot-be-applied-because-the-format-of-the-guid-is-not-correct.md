---
title: „<attribute>" nie może być zastosowane, ponieważ format identyfikatora GUID „<number>" jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: ab821db45ae834e82aa134b6f20ded14d43709ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832271"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>"\<atrybut >" nie można zastosować, ponieważ format identyfikatora GUID "\<liczba >" jest nieprawidłowy
A `COMClassAttribute` bloku attribute określa unikatowy identyfikator globalny (GUID), który jest niezgodny ze odpowiedni format identyfikatora GUID. `COMClassAttribute` używa identyfikatorów GUID do unikatowego identyfikowania tej klasy, interfejsu i zdarzenie tworzenia.  
  
 Identyfikator GUID składa się z 16-bajtowy, z których pierwszych osiem to liczbowe, a ostatnie 8 to: binary. Ona jest generowany przez narzędzia firmy Microsoft, takie jak uuidgen.exe i jest musi być unikatowy w miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do identyfikowania obiektów COM.  
  
2.  Upewnij się, wyświetlone dla ciągów GUID `COMClassAttribute` bloku attribute zostały prawidłowo skopiowane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Guid>
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
