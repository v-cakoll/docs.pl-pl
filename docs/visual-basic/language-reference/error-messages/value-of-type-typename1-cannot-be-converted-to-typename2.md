---
title: Wartości typu „<typename1>” nie można przekonwertować na „<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406563"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Wartości typu „\<typename1>” nie można przekonwertować na „\<typename2>”
\<typename1>Nie można przekonwertować wartości typu "" na " \<typename2> ". Niezgodność typów może być spowodowana mieszaniem odwołania do pliku z odwołaniem projektu do zestawu " \<assemblyname> ". Spróbuj zastąpić odwołanie do pliku " \<filepath> " w projekcie " \<projectname1> " z odwołaniem projektu do " \<projectname2> ".  
  
 W sytuacji, gdy projekt tworzy odwołanie do projektu i odwołanie do pliku, kompilator nie może zagwarantować, że jeden typ może zostać skonwertowany na inny.  
  
 Poniższy pseudo kodu ilustruje sytuację, która może generować ten błąd.  
  
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
  
 Program Project `P1` tworzy pośrednie odwołanie do projektu za pośrednictwem projektu `P2` do projektu `P3` , a także bezpośrednie odwołanie do pliku do `P3` . Deklaracja `commonObject` używa odwołania pliku do `P3` , podczas gdy wywołanie `P2.getCommonClass` używa odwołania do projektu do `P3` .  
  
 Problem w tej sytuacji polega na tym, że odwołanie do pliku Określa ścieżkę i nazwę pliku wyjściowego `P3` (zazwyczaj P3. dll), podczas gdy odwołania projektu identyfikują projekt źródłowy ( `P3` ) według nazwy projektu. W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pośrednictwem dwóch różnych odwołań.  
  
 Ta sytuacja zwykle występuje, gdy odwołania do projektu i odwołania do pliku są mieszane. Na powyższej ilustracji problem nie wystąpi, jeśli zostanie `P1` utworzone bezpośrednie odwołanie do projektu `P3` zamiast odwołania do pliku.  
  
 **Identyfikator błędu:** BC30955  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień odwołanie do pliku na odwołanie do projektu.  
  
## <a name="see-also"></a>Zobacz też

- [Konwersje plików w Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
