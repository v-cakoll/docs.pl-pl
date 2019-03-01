---
title: <typeparamref> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 0ee9e3571ab601f56ddee2fd9a02bb19f50bac62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967363"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru typu. Nazwę należy ująć w znaki podwójnego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metod, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
 Użyj tego tagu, aby umożliwić klientom pliku dokumentacji sformatować wyraz w jakiś sposób distinct, na przykład kursywą.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
