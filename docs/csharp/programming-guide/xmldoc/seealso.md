---
title: '&lt;SeeAlso&gt; (C# przewodnik programowania w języku)'
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
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349138"
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;SeeAlso&gt; (C# przewodnik programowania w języku)
## <a name="syntax"></a>Składnia  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy element podanego kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.`member` musi występować w podwójny cudzysłów ("").  
  
 Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Uwagi  
 \<Seealso > należy określić tekst, który ma być wyświetlane w sekcji Zobacz też. Użyj [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md) można określić łącze od w tekście.  
  
 Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 Zobacz [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) przykład za pomocą \<seealso >.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
