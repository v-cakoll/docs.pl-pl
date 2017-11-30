---
title: "Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3efd4f41184287cdcd3d499712a857bee997c1a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania (Visual Basic)
Jeśli jeden lub więcej argumentów do procedury, każdy argument odnosi się do odpowiedniego elementu programowania kodu wywołującego. Można przekazać wartość tego elementu źródłowego lub odwołanie do niej. Jest to nazywane *przekazywanie mechanizm*.  
  
## <a name="passing-by-value"></a>Przekazywanie poprzez wartość  
 Przekazując argument *przez wartość* , określając [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe dla odpowiadającego mu parametru w definicji procedury. Gdy używasz to przekazywanie mechanizmu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wartość odpowiedniego elementu programowania są kopiowane do zmiennej lokalnej w procedurze. Kod procedury nie ma dostęp do odpowiedniego elementu w wywoływanym kodzie.  
  
## <a name="passing-by-reference"></a>Przekazywanie poprzez odwołanie  
 Przekazując argument *przez odwołanie* , określając [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe dla odpowiadającego mu parametru w definicji procedury. Gdy używasz to przekazywanie mechanizmu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zawiera bezpośrednie odwołanie do odpowiedniego elementu programowania procedury w wywoływanym kodzie.  
  
## <a name="passing-mechanism-and-element-type"></a>Mechanizm przekazywania i typ elementu  
 Przekazywanie mechanizm wyboru nie jest taka sama jak klasyfikacji element podstawowy typu. Przekazywanie według wartości lub według odwołania odwołuje się do co [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dostarcza kod procedury. Typ wartości lub typ referencyjny odwołuje się do przechowywania elementu programistycznego w pamięci.  
  
 Jednak powiązane mechanizm przekazywania i typ elementu. Wartość typu referencyjnego jest wskaźnikiem do danych w pamięci. To oznacza, że jeśli przez wartość typu odwołania, kod procedury ma wskaźnik do odpowiedniego elementu danych, mimo że nie ma dostępu do elementu podstawowego. Na przykład jeśli element jest zmienną tablicową, kod procedury nie ma dostępu do samej zmiennej, ale mogą uzyskiwać dostęp do tablicy elementów członkowskich.  
  
## <a name="ability-to-modify"></a>Uprawnienia do modyfikowania  
 Jeśli element niemodyfikowalnymi jako argument, procedury nigdy nie ją zmodyfikować w kodu wywołującego, czy jest przekazywany `ByVal` lub `ByRef`.  
  
 Dla elementu można modyfikować w poniższej tabeli przedstawiono interakcje między typ elementu i mechanizmu przekazywania.  
  
|Typ elementu|Przekazany`ByVal`|Przekazany`ByRef`|  
|------------------|--------------------|--------------------|  
|Typ wartości (zawiera tylko wartości)|Procedury nie można zmienić, zmiennej lub dowolny z jego elementów członkowskich.|Procedura może zmienić zmienną i jej elementów członkowskich.|  
|Typ odwołania (zawiera wskaźnik do wystąpienia klasy lub struktury)|Nie można zmienić zmiennej procedura, ale można zmienić elementów członkowskich wystąpienia, na którą wskazuje.|Procedura może zmienić zmienna i jej elementów członkowskich wystąpienia, na którą wskazuje.|  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Porady: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Porady: Zmienianie wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Porady: chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Porady: Wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
