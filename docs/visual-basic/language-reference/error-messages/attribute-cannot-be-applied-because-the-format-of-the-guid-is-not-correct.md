---
title: „<attribute>" nie może być zastosowane, ponieważ format identyfikatora GUID „<number>" jest nieprawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 1e92c77e6138bbd546d9b837e095e41d5dfaf30c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279867"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<atrybut >' nie można zastosować, ponieważ format identyfikatora GUID '\<liczba >' jest nieprawidłowy
A `COMClassAttribute` bloku attribute określa unikatowy identyfikator globalny (GUID), który jest niezgodny ze odpowiedni format identyfikatora GUID. `COMClassAttribute` używa identyfikatorów GUID do unikatowego identyfikowania tej klasy, interfejsu i zdarzenie tworzenia.  
  
 Identyfikator GUID składa się z 16-bajtowy, z których pierwszych osiem to liczbowe, a ostatnie 8 to: binary. Ona jest generowany przez narzędzia firmy Microsoft, takie jak uuidgen.exe i jest musi być unikatowy w miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do identyfikowania obiektów COM.  
  
2.  Upewnij się, wyświetlone dla ciągów GUID `COMClassAttribute` bloku attribute zostały prawidłowo skopiowane.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Guid>
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)

