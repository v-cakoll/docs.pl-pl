---
title: <list> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 6e6f3a3399f2bffe84b5cec733833c974a0bb51b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711756"
---
# <a name="list-c-programming-guide"></a>> listy \<(C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametry  
 `term`  
 Termin do zdefiniowania, który zostanie zdefiniowany w `description`.  
  
 `description`  
 Element na liście punktowanej lub numerowanej lub definicji `term`.  
  
## <a name="remarks"></a>Uwagi  
 Blok \<listheader > służy do definiowania wiersza nagłówka tabeli lub listy definicji. Podczas definiowania tabeli należy podać tylko wpis dla terminu w nagłówku.  
  
 Każdy element na liście jest określany za pomocą bloku \<elementu >. Podczas tworzenia listy definicji należy określić zarówno `term`, jak i `description`. Jednak dla tabeli, listy punktowanej lub listy numerowanej należy podać tylko wpis dla `description`.  
  
 Lista lub tabela może zawierać tyle \<elementów > bloków, zgodnie z potrzebami.  
  
 Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
