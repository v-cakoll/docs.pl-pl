---
title: Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837515"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania (Visual Basic)
Jeśli jeden lub więcej argumentów do procedury, każdy argument odnosi się do podstawowego elementu programistycznego, w wywoływanym kodzie. Można przekazać wartość tego bazowego elementu lub odwołanie do niej. Jest to nazywane *mechanizm przekazywania*.  
  
## <a name="passing-by-value"></a>Przekazywanie poprzez wartość  
 Przekazać argument *według wartości* , określając [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe dla odpowiedniego parametru w definicji procedury. Korzystając z tego mechanizmu przekazywania, Visual Basic kopiuje wartość elementu podstawowego programowania do zmiennej lokalnej w procedurze. Kod procedury nie ma dostępu do elementu bazowego w wywoływanym kodzie.  
  
## <a name="passing-by-reference"></a>Przekazywanie poprzez odwołanie  
 Przekazać argument *przez odwołanie* , określając [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe dla odpowiedniego parametru w definicji procedury. Korzystając z tego mechanizmu przekazywania, Visual Basic zapewnia procedury bezpośrednie odwołanie do podstawowego elementu programistycznego kodu wywołującego.  
  
## <a name="passing-mechanism-and-element-type"></a>Mechanizm przekazywania i typ elementu  
 Wybór mechanizm przekazywania nie jest taka sama jak Klasyfikacja typu bazowego elementu. Przekazywanie według wartości lub według odwołania odnosi się do języka Visual Basic dostarcza kod procedury. Typu wartości lub typem referencyjnym odnosi się do przechowywania elementu programowania w pamięci.  
  
 Jednak mechanizm przekazywania i typ elementu są wzajemnie powiązane. Wartość typu referencyjnego jest wskaźnik do danych w innym miejscu w pamięci. To oznacza, że jeśli przekazujesz typu odwołania przez wartość, kod procedury ma wskaźnik do danych elementu podstawowego, nawet jeśli nie można uzyskać dostępu samego elementu bazowego. Na przykład jeśli element jest zmienną tablicową, kod procedury nie ma dostępu do samej zmiennej, ale będzie miał dostęp do tablicy elementów członkowskich.  
  
## <a name="ability-to-modify"></a>Możliwość modyfikowania  
 Jeśli przekazujesz niemodyfikowalnymi elementu jako argument procedury może nigdy nie go modyfikować w kod wywołujący, czy jest przekazywana `ByVal` lub `ByRef`.  
  
 Elementu można modyfikować Poniższa tabela podsumowuje interakcje między typami elementu i mechanizm przekazywania.  
  
|Typ elementu|Przekazany `ByVal`|Przekazany `ByRef`|  
|------------------|--------------------|--------------------|  
|Typ wartości (zawiera tylko wartości)|Procedury nie można zmienić, zmienna lub dowolny z jej członków.|Procedury można zmienić, zmienna i jej elementów członkowskich.|  
|Typ odwołania (zawiera wskaźnik do wystąpienia klasy lub struktury)|Procedura nie można zmienić zmienną, ale można zmienić elementy członkowskie wystąpienia, na którą wskazuje.|Procedury można zmienić, zmienna i jej elementów członkowskich wystąpienia, na którą wskazuje.|  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Instrukcje: Zmień wartość argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
