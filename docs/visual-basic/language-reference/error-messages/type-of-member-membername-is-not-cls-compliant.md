---
title: Typ członka „<membername>” nie jest zgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590685"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>Typ elementu członkowskiego "\<membername >' nie jest zgodny ze specyfikacją CLS
Typ danych określony dla tego elementu członkowskiego nie jest częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS). Nie jest błąd wewnątrz składnika, ponieważ .NET Framework i Visual Basic obsługuje ten typ danych. Jednak inny składnik, napisany w ściśle zgodna ze specyfikacją CLS kod nie może obsługiwać tego typu danych. Takiego składnika nie może być możliwość interakcji pomyślnie z danego składnika.  
  
 Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli składnik interfejsy tylko z innymi składnikami systemu .NET Framework lub nie współpracować z innymi składnikami, nie musisz wprowadzić zmiany.  
  
- Jeśli są komunikowanie się za pomocą składnika nie jest przeznaczony dla .NET Framework, można ustalić, za pomocą odbicia lub dokumentacji, czy obsługuje ona tego typu danych. Jeśli tak jest, nie musisz wprowadzić zmiany.  
  
- Jeśli są komunikowanie się ze składnikiem, który nie obsługuje tego typu danych, można zastąpić go z najbliższego typem zgodnym ze specyfikacją CLS. Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
- Czy komunikowanie się z obiektami automatyzacji lub COM, pamiętać, że niektóre typy mają różnych szerokościach danych niż na platformie .NET Framework. Na przykład `uint` często jest 16 bitów w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.  
  
## <a name="see-also"></a>Zobacz także

- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)
