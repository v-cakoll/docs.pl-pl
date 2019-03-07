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
ms.openlocfilehash: a9b0b9dec09e891105336b3cf0088ed279386d13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471930"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a>Parametry  
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
