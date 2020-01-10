---
title: <see> — C# Przewodnik programowania
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
ms.openlocfilehash: 995b67362bccbc3527f44e5a1d6b659f330e3afd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711717"
---
# <a name="see-c-programming-guide"></a>\<Zobacz > (C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = "`member`"  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML. Umieść *składową* w podwójnym cudzysłowie ("").  
  
## <a name="remarks"></a>Uwagi  
 \<Zobacz > tag pozwala określić łącze z poziomu tekstu. Użyj [\<seealso — >](./seealso.md) , aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też. Użyj [atrybutu cref](./cref-attribute.md) , aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.  
  
 Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
 W poniższym przykładzie pokazano \<Zobacz tag > w sekcji podsumowania.  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
