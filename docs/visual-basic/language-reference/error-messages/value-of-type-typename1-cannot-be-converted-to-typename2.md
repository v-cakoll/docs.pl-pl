---
title: Wartości typu „<typename1>” nie można przekonwertować na „<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: cd2f6e4b51bc327826301d3c7b39c97a4bed3793
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261246"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >"
Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >". Niezgodność typów przyczyną może być połączenie odwołania pliku z odwołaniem projektu do zestawu "\<nazwa_zestawu >". Spróbuj wymienić odwołanie pliku do "\<ścieżka_pliku >' w projekcie"\<projectname1 > "z odwołaniem projektu do"\<projectname2 > ".  
  
 W sytuacji, gdy projekt sprawia, że odwołania projektu i odwołanie do pliku kompilator nie może zagwarantować, że jeden typ może być konwertowany na inny.  
  
 Poniższy pseudo-kod pokazano sytuację, która może wygenerować tego błędu.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projekt `P1` sprawia, że odwołanie do pośredniego projektu za pośrednictwem projektu `P2` do projektu `P3`, a także bezpośrednie odwołanie do pliku `P3`. Deklaracja `commonObject` używa odwołanie pliku do `P3`, podczas gdy wywołaniu `P2.getCommonClass` używa odwołania projektu do `P3`.  
  
 Problem w tej sytuacji jest, że odwołanie do pliku Określa ścieżkę i nazwę pliku dla pliku danych wyjściowych `P3` (zazwyczaj p3.dll), gdy odwołania do projektu zidentyfikować projektu źródłowego (`P3`) według nazwy projektu. W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pośrednictwem dwóch różnych odwołań.  
  
 Taka sytuacja ma zazwyczaj miejsce po projektu odwołania, a mieszane odwołania do pliku. Na poprzedniej ilustracji, problem może nie wystąpić, jeśli `P1` wprowadzone bezpośrednie odwołanie do `P3` zamiast odwołania pliku.  
  
 **Identyfikator błędu:** BC30955  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień odwołanie do pliku z odwołaniem projektu.  
  
## <a name="see-also"></a>Zobacz także
- [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)

