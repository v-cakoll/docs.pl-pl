---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b64372d4b6063da85739e939bb33abd4650ecb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-doc"></a>-doc
Przetwarza komentarzy do dokumentacji do pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. Określanie +, lub po prostu `-doc`, powoduje, że kompilator, aby wygenerować informacje dokumentacji i umieść go w pliku XML. Określanie `-` jest odpowiednikiem nieokreślenie `-doc`, powoduje żadne informacje dokumentacji nie ma zostać utworzony.|  
|`file`|Jeśli wymagane `-doc:` jest używany. Określa wyjściowego pliku XML, który jest wypełniana komentarze z plików kodu źródłowego kompilacji. Jeśli nazwa pliku zawiera spację, należy ująć nazwę w cudzysłowie ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-doc` Opcję formantów, czy kompilator generuje plik XML zawierający komentarze dokumentacji. Jeśli używasz `-doc:file` składni `file` parametr określa nazwę pliku XML. Jeśli używasz `-doc` lub `-doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilatora. Jeśli używasz `-doc-` lub nie określaj `-doc` opcja, kompilator nie tworzy pliku XML.  
  
 W plikach kodu źródłowego komentarzy do dokumentacji może poprzedzać następujące definicje:  
  
-   Zdefiniowane przez użytkownika typów, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [— interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Elementy członkowskie, takich jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwości](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Aby utworzony plik XML za pomocą programu Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku pliku XML, jest taka sama jak zestawu mają być obsługiwane. Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu w przypadku zestawu odwołuje się projekt programu Visual Studio, pliku XML, który znajduje się także. Pliki dokumentacji XML nie są wymagane przez funkcję IntelliSense dla kodu w ramach projektu lub projektów odwołuje się projekt.  
  
 O ile kompilacji z `/target:module`, plik XML zawierający tagi `<assembly></assembly>`. Znaczniki Określ nazwę pliku zawierającego manifest zestawu dla pliku danych wyjściowych kompilacji.  
  
 Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.  
  
|Można ustawić - doc w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Ustaw wartość **Generuj plik dokumentacji XML** pole.|  
  
## <a name="example"></a>Przykład  
 Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) przykładowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
