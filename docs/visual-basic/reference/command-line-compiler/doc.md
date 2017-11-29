---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2490529b951ef6e583e3bfa54afced89c823e874
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="doc"></a>/doc
Przetwarza komentarzy do dokumentacji do pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. Określanie +, lub po prostu `/doc`, powoduje, że kompilator, aby wygenerować informacje dokumentacji i umieść go w pliku XML. Określanie `-` jest odpowiednikiem nieokreślenie `/doc`, powoduje żadne informacje dokumentacji nie ma zostać utworzony.|  
|`file`|Jeśli wymagane `/doc:` jest używany. Określa wyjściowego pliku XML, który jest wypełniana komentarze z plików kodu źródłowego kompilacji. Jeśli nazwa pliku zawiera spację, należy ująć nazwę w cudzysłowie ("").|  
  
## <a name="remarks"></a>Uwagi  
 `/doc` Opcję formantów, czy kompilator generuje plik XML zawierający komentarze dokumentacji. Jeśli używasz `/doc:``file` składni `file` parametr określa nazwę pliku XML. Jeśli używasz `/doc` lub `/doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilatora. Jeśli używasz `/doc-` lub nie określaj `/doc` opcja, kompilator nie tworzy pliku XML.  
  
 W plikach kodu źródłowego komentarzy do dokumentacji może poprzedzać następujące definicje:  
  
-   Zdefiniowane przez użytkownika typów, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [— interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Elementy członkowskie, takich jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwości](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Aby użyć wygenerowanego pliku XML z [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku pliku XML, jest taka sama jak zestawu mają być obsługiwane. Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu podczas odwołuje się zestaw [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projekt, plik XML znajduje się także. Pliki dokumentacji XML nie są wymagane przez funkcję IntelliSense dla kodu w ramach projektu lub projektów odwołuje się projekt.  
  
 O ile kompilacji z `/target:module`, plik XML zawierający tagi `<assembly></assembly>`. Znaczniki Określ nazwę pliku zawierającego manifest zestawu dla pliku danych wyjściowych kompilacji.  
  
 Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.  
  
|Aby ustawić/doc w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Ustaw wartość **Generuj plik dokumentacji XML** pole.|  
  
## <a name="example"></a>Przykład  
 Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) przykładowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
