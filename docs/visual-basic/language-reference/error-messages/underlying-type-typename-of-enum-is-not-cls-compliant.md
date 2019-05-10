---
title: Typ źródłowy <typename> wyliczenia jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: b58759502b9297f9cd5ac89296ab147c40fc89f1
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913358"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a>Typ bazowy \<typename > wyliczenia jest niezgodny ze specyfikacją CLS
Typ danych określony dla tego wyliczenia jest częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS). Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i język Visual Basic obsługuje ten typ danych. Jednak inny składnik, napisany w ściśle zgodna ze specyfikacją CLS kod nie może obsługiwać tego typu danych. Takiego składnika nie może być możliwość interakcji pomyślnie z danego składnika.  
  
 Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40032  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składników lub czy nie współpracować z innymi składnikami, nie trzeba wprowadzić zmiany.  
  
- Jeśli są komunikowanie się za pomocą składnika nie jest przeznaczony dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub dokumentacji, czy ten typ danych. Jeśli tak jest, nie musisz wprowadzić zmiany.  
  
- Jeśli są komunikowanie się ze składnikiem, który nie obsługuje tego typu danych, można zastąpić go z najbliższego typem zgodnym ze specyfikacją CLS. Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
- Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Na przykład `uint` często jest 16 bitów w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)
