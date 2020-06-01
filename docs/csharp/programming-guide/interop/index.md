---
title: Współdziałanie — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e53465066cf27a5f46c66ac73ee242370be23395
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242010"
---
# <a name="interoperability-c-programming-guide"></a>Współdziałanie (Przewodnik programowania w języku C#)

Współdziałanie pozwala zachować istniejące inwestycje w kodzie niezarządzanym i korzystać z nich. Kod, który jest uruchamiany pod kontrolą środowiska uruchomieniowego języka wspólnego (CLR) jest nazywany *kodem zarządzanym*, a kod, który jest URUCHAMIANY poza środowiskiem CLR, jest nazywany *kodem niezarządzanym*. Przykłady kodu niezarządzanego modelu COM, COM+, C++, Components, ActiveX i Microsoft Windows API.  
  
Platforma .NET umożliwia współdziałanie z kodem niezarządzanym za pomocą usług wywołania platformy, <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałania C++ i współdziałania modelu COM (międzyoperacyjna com)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd współdziałania](./interoperability-overview.md)  
 Opisuje metody współpracy między kodem zarządzanym C# i niezarządzanym kodem.  
  
 [Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#](./how-to-access-office-onterop-objects.md)  
 Zawiera opis funkcji wprowadzonych w Visual C# w celu ułatwienia programowania pakietu Office.  
  
 [Używanie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Opisuje sposób używania właściwości indeksowanych w celu uzyskania dostępu do właściwości COM, które mają parametry.  
  
 [Używanie wywołania platformy do odtwarzania pliku WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Opisuje, jak używać usług wywołania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.  
  
 [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)  
 Pokazuje, jak utworzyć skoroszyt programu Excel i dokument programu Word, który zawiera link do skoroszytu.  
  
 [Klasa COM — Przykład](./example-com-class.md)  
 Pokazuje, jak uwidocznić klasę języka C# jako obiekt COM.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)
