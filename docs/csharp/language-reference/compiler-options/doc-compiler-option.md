---
title: -doc (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: ac1275285a8ba403297e51438fbf0d47d811ca61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-doc-c-compiler-options"></a>-doc (opcje kompilatora C#)
**-Doc** opcja pozwala na umieszczenie komentarzy do dokumentacji w pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Plik wyjściowy XML, który jest wypełniana komentarze w plikach źródłowych kodu kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 W pliki kodu źródłowego komentarzy do dokumentacji poprzedzających poniżej można przetworzyć i dodane do pliku XML:  
  
-   Takie typy danych zdefiniowane przez użytkownika jako [klasy](../../../csharp/language-reference/keywords/class.md), [delegować](../../../csharp/language-reference/keywords/delegate.md), lub [— interfejs](../../../csharp/language-reference/keywords/interface.md)  
  
-   Takie elementy członkowskie jako pole, [zdarzeń](../../../csharp/language-reference/keywords/event.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md), lub — metoda  
  
 Pliku kodu źródłowego, który zawiera główny najpierw są kierowane do pliku XML.  
  
 Aby użyć pliku .xml wygenerowany do użycia z [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku w pliku XML, być takie same jak zestawu ma być obsługuje, a następnie sprawdź, czy plik XML znajduje się w tym samym katalogu co zestaw. W związku z tym gdy zestaw odwołuje się projekt programu Visual Studio, plik XML znajduje się także. Zobacz [dostarczanie komentarze w kodzie](/visualstudio/ide/supplying-xml-code-comments) i uzyskać więcej informacji.  
  
 O ile kompilacji z [-docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` będzie zawierać \<zestawu > \< /Assembly > tagi, określając nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
> [!NOTE]
>  Doc — opcja ma zastosowanie do wszystkich wejściowych plików; lub, w przypadku ustawienia w ustawieniach projektu, wszystkie pliki w projekcie. Aby wyłączyć ostrzeżenia dotyczące komentarzy do dokumentacji dla określonego pliku lub części kodu, należy użyć [ostrzeżenie #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Zobacz [tagi zalecane dla komentarzy do dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** kartę.  
  
3.  Modyfikowanie **pliku dokumentacji XML** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
