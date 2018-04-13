---
title: -imports (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
Importuje przestrzeni nazw z określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespaceList`|Wymagany. Rozdzielana przecinkami lista obszarów nazw do zaimportowania.|  
  
## <a name="remarks"></a>Uwagi  
 `-imports` Opcja importuje przestrzeni nazw zdefiniowane w obrębie bieżącego zestawu plików źródłowych lub z dowolnej przywoływanego zestawu.  
  
 Elementy członkowskie w przestrzeni nazw określony za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji. Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do użycia w pliku kodu źródłowego w jednej przestrzeni nazw.  
  
|Aby ustawić/Import w Visual Studio zintegrowane środowisko programistyczne|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **odwołania** kartę.<br />3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać importu użytkownika** przycisku.<br />4.  Kliknij przycisk **dodać importu użytkownika** przycisku.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje kiedy `/imports:system.globalization` jest określona. Bez tego pomyślnej kompilacji wymaga albo `Imports System.Globalization` instrukcji być uwzględnione na początku pliku źródła kodu, lub że właściwość być w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name`. 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
