---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588447"
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
Importuje przestrzenie nazw z określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespaceList`|Wymagana. Rozdzielana przecinkami lista przestrzeni nazw do zaimportowania.|  
  
## <a name="remarks"></a>Uwagi  
 `-imports` Opcja importuje dowolnego obszaru nazw, zdefiniowany w ramach bieżącego zestawu plików źródłowych lub z dowolnym przywoływanego zestawu.  
  
 Członkowie w przestrzeni nazw określony za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji. Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do korzystania z przestrzeni nazw w pliku kodu źródłowego w jednym.  
  
|Aby ustawić/Import w programie Visual Studio zintegrowanego środowiska programistycznego|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **odwołania** kartę.<br />3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać Import użytkownika** przycisku.<br />4.  Kliknij przycisk **dodać Import użytkownika** przycisku.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje, kiedy `/imports:system.globalization` jest określony. Bez tego pomyślnej kompilacji wymaga obu `Imports System.Globalization` instrukcja być uwzględniona na początku pliku kodu źródłowego, lub właściwości można w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name`. 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
