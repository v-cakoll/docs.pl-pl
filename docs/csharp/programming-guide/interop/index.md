---
title: Współdziałanie — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712055"
---
# <a name="interoperability-c-programming-guide"></a>Współdziałanie (Przewodnik programowania w języku C#)
Współdziałanie pozwala zachować istniejące inwestycje w kodzie niezarządzanym i korzystać z nich. Kod, który jest uruchamiany pod kontrolą środowiska uruchomieniowego języka wspólnego (CLR) jest nazywany *kodem zarządzanym*, a kod, który jest URUCHAMIANY poza środowiskiem CLR, jest nazywany *kodem niezarządzanym*. COM, COM+, C++ składniki, składniki ActiveX i interfejs API systemu Microsoft Windows to przykłady kodu niezarządzanego.  
  
 .NET Framework umożliwia współdziałanie z kodem niezarządzanym za pomocą usług wywołania platformy, C++ <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałania i współdziałania modelu COM (międzyoperacyjność com).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd współdziałania](./interoperability-overview.md)  
 Opisuje metody współpracy między C# kodem zarządzanym i niezarządzanym kodem.  
  
 [Jak uzyskać dostęp do obiektów międzyoperacyjności C# pakietu Office za pomocą funkcji](./how-to-access-office-onterop-objects.md)  
 Zawiera opis funkcji wprowadzonych w wizualizacji C# w celu ułatwienia programowania pakietu Office.  
  
 [Jak używać właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Opisuje sposób używania właściwości indeksowanych w celu uzyskania dostępu do właściwości COM, które mają parametry.  
  
 [Jak odtworzyć plik WAV przy użyciu wywołania platformy](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Opisuje, jak używać usług wywołania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.  
  
 [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)  
 Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word, który zawiera link do skoroszytu.  
  
 [Przykładowa klasa modelu COM](./example-com-class.md)  
 Pokazuje, jak uwidocznić C# klasę jako obiekt com.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)
