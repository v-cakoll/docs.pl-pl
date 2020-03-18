---
title: Interoperacyjność — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712055"
---
# <a name="interoperability-c-programming-guide"></a>Współdziałanie (Przewodnik programowania w języku C#)
Współdziałanie umożliwia zachowanie i wykorzystanie istniejących inwestycji w kod niezarządzany. Kod, który jest uruchamiany pod kontrolą wspólnego języka runtime (CLR) jest nazywany *kodem zarządzanym,* a kod, który działa poza CLR jest nazywany *kodem niezarządzanym*. Przykłady niezarządzanego kodu COM+, C++, składników ActiveX i interfejsu API systemu Microsoft Windows.  
  
 Program .NET Framework umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem usług wywoływania platformy, przestrzeni <xref:System.Runtime.InteropServices> nazw, współdziałania języka C++ i współdziałania modelu COM (COM interop).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd współdziałania](./interoperability-overview.md)  
 W tym artykule opisano metody współdziałania między kodem zarządzanym języka C# a kodem niezarządzanym.  
  
 [Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#](./how-to-access-office-onterop-objects.md)  
 W tym artykule opisano funkcje wprowadzone w języku Visual C# w celu ułatwienia programowania pakietu Office.  
  
 [Używanie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 W tym artykule opisano, jak używać właściwości indeksowanych do uzyskiwania dostępu do właściwości COM, które mają parametry.  
  
 [Używanie wywołania platformy do odtwarzania pliku WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 W tym artykule opisano, jak używać usług wywoływania platformy do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.  
  
 [Instruktaż: Programowanie pakietu Office](./walkthrough-office-programming.md)  
 Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word zawierający łącze do skoroszytu.  
  
 [Przykładowa klasa modelu COM](./example-com-class.md)  
 Pokazuje, jak udostępnić klasy C# jako obiekt COM.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Instruktaż: Programowanie pakietu Office](./walkthrough-office-programming.md)
