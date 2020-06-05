---
title: Typ członka „<membername>” nie jest zgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 030cb31b8f1ba0e8eaa82eeb8e37153411a53404
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400308"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>Typ członka „\<membername>” nie jest zgodny ze specyfikacją CLS
Typ danych określony dla tego elementu członkowskiego nie jest częścią [niezależną od języka i składników niezależnych od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS). Nie jest to błąd w składniku, ponieważ .NET Framework i Visual Basic obsługują ten typ danych. Jednak inny składnik zapisany w kodzie zgodnym ze specyfikacją CLS może nie obsługiwać tego typu danych. Taki składnik może nie być w stanie pomyślnie korzystać z składnika.  
  
 Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../data-types/ushort-data-type.md)  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli składnik obsługuje tylko inne składniki .NET Framework lub nie ma interfejsu z innymi składnikami, nie trzeba zmieniać żadnych elementów.  
  
- Jeśli korzystasz z składnika, który nie został zapisany dla .NET Framework, możesz określić, poprzez odbicie lub z dokumentacji, czy obsługuje ten typ danych. W przeciwnym razie nie trzeba zmieniać żadnych elementów.  
  
- W przypadku współdziałania ze składnikiem, który nie obsługuje tego typu danych, należy zamienić go na najbliższy typ zgodny ze specyfikacją CLS. Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .  
  
- Jeśli masz połączenie z obiektami automatyzacji lub COM, pamiętaj, że niektóre typy mają różne szerokości danych niż w .NET Framework. Na przykład `uint` często jest 16 bitów w innych środowiskach. Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.  
  
## <a name="see-also"></a>Zobacz też

- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)
