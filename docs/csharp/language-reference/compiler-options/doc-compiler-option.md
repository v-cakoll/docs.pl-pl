---
title: -doc (C# opcje kompilatora)
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
ms.openlocfilehash: 7b22bbf75b29fdffd9927110ebe5b4e5309cd778
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191836"
---
# <a name="-doc-c-compiler-options"></a>-doc (C# opcje kompilatora)
Opcja **-doc** umożliwia umieszczenie komentarzy do dokumentacji w pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Plik wyjściowy dla XML, który jest wypełniony komentarzami w plikach kodu źródłowego kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 W plikach kodu źródłowego Komentarze do dokumentacji, które poprzedzają następujące elementy, mogą być przetwarzane i dodawane do pliku XML:  
  
- Takie typy zdefiniowane przez użytkownika jako [Klasa](../keywords/class.md), [Delegat](../keywords/delegate.md)lub [interfejs](../keywords/interface.md)  
  
- Takie elementy członkowskie jak pole, [zdarzenie](../keywords/event.md), [Właściwość](../../programming-guide/classes-and-structs/using-properties.md)lub metoda  
  
 Plik kodu źródłowego, który zawiera główny, jest wyprowadzany jako pierwszy w formacie XML.  
  
 Aby użyć wygenerowanego pliku XML do użycia z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) , pozwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany, a następnie upewnij się, że plik. XML znajduje się w tym samym katalogu, co zestaw. Z tego względu, gdy zestaw jest przywoływany w projekcie programu Visual Studio, można również znaleźć plik. XML. Zobacz [dostarczanie komentarzy do kodu](/visualstudio/ide/reference/generate-xml-documentation-comments) i aby uzyskać więcej informacji.  
  
 O ile nie zostanie skompilowany [moduł-target: module](./target-module-compiler-option.md), `file` będzie zawierać \<assembly >\</Assembly > Tagi, określając nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
> [!NOTE]
> Opcja-doc dotyczy wszystkich plików wejściowych; lub, jeśli jest ustawiony w ustawieniach projektu, wszystkie pliki w projekcie. Aby wyłączyć ostrzeżenia związane z komentarzami do dokumentacji dla określonego pliku lub sekcji kodu, użyj [#pragma ostrzeżenie](../preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Zapoznaj się z [polecanymi tagami komentarzy do dokumentacji](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij kartę **kompilacja** .  
  
3. Zmodyfikuj właściwość **pliku dokumentacji XML** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
