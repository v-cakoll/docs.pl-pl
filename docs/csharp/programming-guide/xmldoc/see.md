---
title: '&lt;zobacz&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 63476ff77f1a8286730f29149bb5b6b87779f144
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058415"
---
# <a name="ltseegt-c-programming-guide"></a>&lt;zobacz&gt; (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML. Miejsce *elementu członkowskiego* w znaki podwójnego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 \<Zobacz > należy określić łącze między w tekście. Użyj [ \<SeeAlso — >](../../../csharp/programming-guide/xmldoc/seealso.md) do wskazania, że tekst powinny być umieszczone w sekcji Zobacz też. Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) do utworzenia wewnętrznego hiperlinki do stron dokumentacji dla elementów kodu.  
  
 Kompiluj przy użyciu [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
 W poniższym przykładzie przedstawiono \<zobacz > tagu w sekcji podsumowania.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
