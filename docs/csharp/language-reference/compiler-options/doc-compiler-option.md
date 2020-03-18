---
title: -doc (Opcje kompilatora C#)
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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422970"
---
# <a name="-doc-c-compiler-options"></a>-doc (Opcje kompilatora C#)
Opcja **-doc** umożliwia umieszczanie komentarzy dokumentacji w pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Plik wyjściowy dla języka XML, który jest wypełniany komentarzami w plikach kodu źródłowego kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 W plikach kodu źródłowego komentarze dokumentacji, które poprzedzają następujące czynności, mogą być przetwarzane i dodawane do pliku XML:  
  
- Takie typy zdefiniowane przez użytkownika jako [klasa,](../keywords/class.md) [delegat](../builtin-types/reference-types.md#the-delegate-type)lub [interfejs](../keywords/interface.md)  
  
- Takie elementy członkowskie, jak pole, [zdarzenie,](../keywords/event.md) [właściwość](../../programming-guide/classes-and-structs/using-properties.md)lub metoda  
  
 Plik kodu źródłowego, który zawiera Main jest najpierw wyprowadzany do pliku XML.  
  
 Aby użyć wygenerowanego pliku xml do użycia z funkcją [IntelliSense,](/visualstudio/ide/using-intellisense) niech nazwa pliku xml będzie taka sama jak zestaw, który chcesz obsługiwać, a następnie upewnij się, że plik xml znajduje się w tym samym katalogu co zestaw. W związku z tym gdy zestaw odwołuje się do projektu programu Visual Studio, plik xml znajduje się również. Zobacz [dostarczanie komentarzy do kodu](/visualstudio/ide/reference/generate-xml-documentation-comments) i uzyskać więcej informacji.  
  
 Chyba że skompilować z [-target:module](./target-module-compiler-option.md), `file` będzie zawierać \<zestaw>\</zestaw> tagów określających nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.  
  
> [!NOTE]
> Opcja -doc ma zastosowanie do wszystkich plików wejściowych; lub, jeśli ustawiono w ustawieniach projektu, wszystkie pliki w projekcie. Aby wyłączyć ostrzeżenia związane z komentarzami dokumentacji dla określonego pliku lub sekcji kodu, należy użyć [ostrzeżenia #pragma](../preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Zobacz [Zalecane tagi dla dokumentacji Komentarze](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) dla sposobów generowania dokumentacji z komentarzy w kodzie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij kartę **Kompilacja.**  
  
3. Zmodyfikuj właściwość **pliku dokumentacji XML.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>kompilatora, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
