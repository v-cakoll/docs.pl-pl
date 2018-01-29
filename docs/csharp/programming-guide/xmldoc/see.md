---
title: "&lt;zobacz&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 959da56269081ebee036c620e535185609c5bff3
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="ltseegt-c-programming-guide"></a>&lt;zobacz&gt; (C# przewodnik programowania w języku)
## <a name="syntax"></a>Składnia  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy element podanego kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML. Miejsce *elementu członkowskiego* w podwójny cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 \<Zobacz > należy określić łącze znajdujących się w tekście. Użyj [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) aby wskazać, że tekst powinna zostać umieszczona w sekcji Zobacz też. Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) można utworzyć wewnętrznego hiperłącza do stron dokumentacji dla elementów kodu.  
  
 Kompiluj z użyciem [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
 W poniższym przykładzie przedstawiono \<zobacz > tagu w sekcji podsumowania.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
