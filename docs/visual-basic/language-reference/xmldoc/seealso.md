---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 27bb2c271631170082709d9e3d76cd39eefbc860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352217"
---
# <a name="seealso-visual-basic"></a>\<seealso — > (Visual Basic)
Określa łącze, które pojawia się w sekcji Zobacz też.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML. `member` musi znajdować się w podwójnym cudzysłowie ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj znacznika `<seealso>`, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też. Użyj [\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) , aby określić łącze z tekstu.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano tag `<seealso>` w sekcji `DoesRecordExist` uwagi, aby odwołać się do metody `UpdateRecord`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
