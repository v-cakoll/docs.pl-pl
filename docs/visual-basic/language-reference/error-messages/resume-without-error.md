---
title: Wznowienie bez błędu
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400373"
---
# <a name="resume-without-error"></a>Wznowienie bez błędu
`Resume`Instrukcja pojawiła się poza kodem obsługi błędu lub kod przeskoczy do procedury obsługi błędów, chociaż nie wystąpił błąd.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Przenieś `Resume` instrukcję do procedury obsługi błędów lub usuń ją.  
  
2. Przeskocz do etykiet nie mogą występować w różnych procedurach, więc Wyszukaj w tej procedurze etykietę identyfikującą procedurę obsługi błędów. Jeśli zostanie znaleziona zduplikowana etykieta określona jako obiekt docelowy `GoTo` instrukcji, która nie jest `On Error GoTo` instrukcją, Zmień etykietę wiersza, aby zgadzać się z zamierzonym celem.  
  
## <a name="see-also"></a>Zobacz też

- [Resume — Instrukcja](../statements/resume-statement.md)
- [On Error, instrukcja](../statements/on-error-statement.md)
