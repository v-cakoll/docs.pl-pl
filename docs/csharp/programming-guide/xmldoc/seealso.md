---
title: '&lt;SeeAlso —&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e75480db9aebdeb2199694168abf4f774773b9c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543555"
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;SeeAlso —&gt; (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.`member` musi znajdować się w znaki podwójnego cudzysłowu ("").  
  
 Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Uwagi  
 \<SeeAlso — > należy określić tekst, który możesz chcieć pojawiają się w sekcji Zobacz też. Użyj [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md) określić łącze między w tekście.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 Zobacz [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) na przykład za pomocą \<SeeAlso — >.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
