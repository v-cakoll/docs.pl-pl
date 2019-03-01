---
title: <summary> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 12898d5cd10d9ecca4ec0fd1f7d06be0761b57b8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978556"
---
# <a name="summary-c-programming-guide"></a>\<Podsumowanie > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Podsumowanie obiektu.  
  
## <a name="remarks"></a>Uwagi  
 \<Podsumowania > tag powinien być używany do opisu typu lub składowej typu. Użyj [ \<Uwagi >](../../../csharp/programming-guide/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu. Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) umożliwiające dokumentacji narzędzia, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do utworzenia wewnętrznego hiperlinki do stron dokumentacji dla elementów kodu.  
  
 Tekst dla \<podsumowania > tag to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w oknie przeglądarki obiektów.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku. Aby utworzyć dokumentację na podstawie pliku generowanych przez kompilator, można utworzyć narzędzie niestandardowe, lub użyj narzędzia takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 Poprzedni przykład tworzy następującego pliku XML.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wprowadzić `cref` odwołanie do typu ogólnego.  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 Poprzedni przykład tworzy następującego pliku XML.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
