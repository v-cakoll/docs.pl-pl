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
ms.openlocfilehash: 4c77d063d64354bf4693ce82509f36be9d2e5b0c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670967"
---
# <a name="-doc"></a>-doc
Przetwarza komentarze dokumentacji do pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. Określanie +, lub po prostu `-doc`, powoduje, że kompilator do generowania informacji o dokumentacji i umieść go w pliku XML. Określanie `-` jest odpowiednikiem nie został podany `-doc`, powodując Brak informacji o dokumentacji, ma zostać utworzony.|  
|`file`|Jeśli wymagane `-doc:` jest używany. Określa wyjściowy plik XML, który jest wypełniana przy użyciu komentarzy z plików kodu źródłowego, kompilacji. Jeśli nazwa pliku zawiera spację, należy ująć nazwę ze znakami cudzysłowu ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-doc` Opcji kontrolki, czy kompilator generuje plik XML zawierający komentarze dokumentacji. Jeśli używasz `-doc:file` składni `file` parametr określa nazwę pliku XML. Jeśli używasz `-doc` lub `-doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilator. Jeśli używasz `-doc-` lub nie określaj `-doc` opcja, kompilator nie tworzy pliku XML.  
  
 W plikach kodu źródłowego komentarze dokumentacji może poprzedzać następujące definicje:  
  
-   Zdefiniowane przez użytkownika typy, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [interfejsu](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Elementy członkowskie, takie jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwość](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Wygenerowany plik XML za pomocą programu Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, niech nazwę pliku pliku XML, być taka sama jak zestawu mają być obsługiwane. Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu w przypadku zestawu odwołuje się do projektu programu Visual Studio, pliku XML, który znajduje się także. Pliki dokumentacji XML nie są wymagane, aby technologia IntelliSense działała dla kodu w projekcie lub w obrębie projektów odwołuje się projekt.  
  
 Jeśli kompilujesz z `/target:module`, plik XML zawiera tagi `<assembly></assembly>`. Te znaczniki, określ nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
 Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md) sposobów generować dokumentację z komentarzy w kodzie.  
  
|Aby ustawić - dokumentu w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Ustaw wartość w **soubor dokumentace XML do generowania** pole.|  
  
## <a name="example"></a>Przykład  
 Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) dla próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
