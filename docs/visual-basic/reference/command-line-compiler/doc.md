---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 3da049b912d791f26814bb4b6cbb70998803726a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005650"
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
|`+` &#124; `-`|Opcjonalny. Określenie wartości + lub po prostu `-doc` powoduje, że kompilator generuje informacje dokumentacji i umieszcza je w pliku XML. Określenie `-` jest odpowiednikiem nieokreślenia `-doc`, co nie powoduje utworzenia informacji o dokumentacji.|  
|`file`|Wymagane, jeśli użyto `-doc:`. Określa wyjściowy plik XML, który jest wypełniany komentarzami z plików kodu źródłowego kompilacji. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-doc` Określa, czy kompilator generuje plik XML zawierający komentarze dokumentacji. Jeśli używasz składni `-doc:file`, parametr `file` określa nazwę pliku XML. Jeśli używasz `-doc` lub `-doc+`, kompilator Pobiera nazwę pliku XML z pliku wykonywalnego lub biblioteki tworzonego przez kompilator. Jeśli używasz `-doc-` lub nie określisz opcji `-doc`, kompilator nie utworzy pliku XML.  
  
 W plikach kodu źródłowego Komentarze do dokumentacji mogą poprzedzać następujące definicje:  
  
- Typy zdefiniowane przez użytkownika, takie jak [Klasa](../../../visual-basic/language-reference/statements/class-statement.md) lub [interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
- Elementy członkowskie, takie jak pole, [zdarzenie](../../../visual-basic/language-reference/statements/event-statement.md), [Właściwość](../../../visual-basic/language-reference/statements/property-statement.md), [Funkcja](../../../visual-basic/language-reference/statements/function-statement.md)lub [podprocedura](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Aby użyć wygenerowanego pliku XML z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) programu Visual Studio, Zezwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany. Upewnij się, że plik XML znajduje się w tym samym katalogu, co zestaw, aby w przypadku odwołania do zestawu w projekcie programu Visual Studio również znaleźć plik. XML. Pliki dokumentacji XML nie są wymagane, aby funkcja IntelliSense mogła korzystać z kodu w projekcie lub w obrębie projektów, do których odwołuje się projekt.  
  
 Chyba że kompilujesz z `/target:module`, plik XML zawiera Tagi `<assembly></assembly>`. Te znaczniki określają nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
 Zobacz [Tagi komentarzy XML](../../../visual-basic/language-reference/xmldoc/index.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.  
  
|Aby ustawić doc w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. Ustaw wartość w polu **Generuj plik dokumentacji XML** .|  
  
## <a name="example"></a>Przykład  
 Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) dla przykładu.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
