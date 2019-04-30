---
title: Współdziałanie — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 50f2a72bf4981a49d5597a9bc8922db81197d810
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710228"
---
# <a name="interoperability-c-programming-guide"></a>Współdziałanie (Przewodnik programowania w języku C#)
Współdziałanie pozwala na zachowanie i wykorzystać istniejące inwestycje w niezarządzanym kodzie. Kod, który działa pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, a kod, który działa poza środowisko CLR jest nazywana *kod niezarządzany*. COM, COM +, składniki C++, składników ActiveX i interfejsu API programu Microsoft Windows są przykłady kodu niezarządzanego.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie z COM (Usługa międzyoperacyjna modelu COM).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 W tym artykule opisano metody pod kątem współdziałania między kod zarządzany języka C#, a kod niezarządzany.  
  
 [Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 W tym artykule opisano funkcje, które zostały wprowadzone w języku Visual C# do ułatwienia programowania pakietu Office.  
  
 [Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 W tym artykule opisano, jak używać właściwości indeksowanych na dostęp do właściwości modelu COM, które mają parametry.  
  
 [Instrukcje: Użycie wywołania platformy do odtwarzania pliku Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Opisuje sposób używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.  
  
 [Przewodnik: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Pokazuje, jak utworzyć skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.  
  
 [Przykładowa klasa modelu COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Pokazuje, jak udostępnić klasy C# jako obiekt COM.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)
- [Przewodnik: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
