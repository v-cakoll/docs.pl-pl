---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: a818fd46bd93682f0bede1d22b8cbc2ca6467a40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716742"
---
# <a name="-doc"></a>-doc
Przetwarza komentarze dokumentacji do pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-doc[+ | -]  
```

lub  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+`&#124;`-`|Element opcjonalny. Określenie +, lub po `-doc`prostu powoduje, że kompilator generuje informacje dokumentacji i umieszcza je w pliku XML. Określenie `-` jest odpowiednikiem nieokreślenia `-doc`, co nie powoduje utworzenia informacji o dokumentacji.|  
|`file`|Wymagane, `-doc:` jeśli jest używany. Określa wyjściowy plik XML, który jest wypełniany komentarzami z plików kodu źródłowego kompilacji. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-doc` Opcja określa, czy kompilator GENERUJE plik XML zawierający komentarze dokumentacji. Jeśli używasz `-doc:file` składni, `file` parametr określa nazwę pliku XML. Jeśli używasz `-doc` lub `-doc+`, KOMPILATOR Pobiera nazwę pliku XML z pliku wykonywalnego lub biblioteki, którą tworzy kompilator. Jeśli używasz `-doc-` lub nie określisz `-doc` opcji, KOMPILATOR nie tworzy pliku XML.  
  
 W plikach kodu źródłowego Komentarze do dokumentacji mogą poprzedzać następujące definicje:  
  
- Typy zdefiniowane przez użytkownika, takie jak [Klasa](../../../visual-basic/language-reference/statements/class-statement.md) lub [interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
- Elementy członkowskie, takie jak pole, [zdarzenie](../../../visual-basic/language-reference/statements/event-statement.md), [Właściwość](../../../visual-basic/language-reference/statements/property-statement.md), [Funkcja](../../../visual-basic/language-reference/statements/function-statement.md)lub [podprocedura](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Aby użyć wygenerowanego pliku XML z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) programu Visual Studio, Zezwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany. Upewnij się, że plik XML znajduje się w tym samym katalogu, co zestaw, aby w przypadku odwołania do zestawu w projekcie programu Visual Studio również znaleźć plik. XML. Pliki dokumentacji XML nie są wymagane, aby funkcja IntelliSense mogła korzystać z kodu w projekcie lub w obrębie projektów, do których odwołuje się projekt.  
  
 Chyba że kompilujesz `-target:module`program, plik XML zawiera Tagi `<assembly></assembly>`. Te znaczniki określają nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
 Zobacz [Tagi komentarzy XML](../../../visual-basic/language-reference/xmldoc/index.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.  
  
|Aby ustawić doc w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. Ustaw wartość w polu **Generuj plik dokumentacji XML** .|  
  
## <a name="example"></a>Przykład  
 Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) dla przykładu.  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
