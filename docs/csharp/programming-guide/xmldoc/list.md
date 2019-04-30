---
title: <list> - C# Przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: 9ac1d749d18a9d02ce28f8cf600495f345ec0e89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708044"
---
# <a name="list-c-programming-guide"></a>\<Lista > (C# Programming Guide)
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
 Termin, aby zdefiniować, które są definiowane w `description`.  
  
 `description`  
 Element w punktora lub Lista numerowana lub definicji `term`.  
  
## <a name="remarks"></a>Uwagi  
 \<Listheader > Blokuj służy do definiowania wiersz nagłówka tabeli lub definicji listy. Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.  
  
 Każdy element na liście jest określony za pomocą \<elementu > bloku. Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`. Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.  
  
 Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
