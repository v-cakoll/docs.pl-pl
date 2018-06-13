---
title: Współdziałanie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332884"
---
# <a name="interoperability-c-programming-guide"></a>Współdziałanie (Przewodnik programowania w języku C#)
Współdziałanie umożliwia zachowanie i wykorzystać istniejące inwestycje w technologie kodu niezarządzanego. Kod uruchamiany pod kontrolą środowisko uruchomieniowe języka wspólnego (CLR) jest nazywany *kodu zarządzanego*, i jest nazywany kodu uruchamianego poza środowiskiem CLR *niezarządzany kod*. COM, COM +, składniki C++, składników ActiveX i interfejsu API Win32 usługi Microsoft są przykłady kodu niezarządzanego.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umożliwia współdziałanie z kodem niezarządzanym za pośrednictwem platformy wywołania usług, <xref:System.Runtime.InteropServices> przestrzeni nazw, współdziałanie języka C++ i współdziałanie COM (Usługa międzyoperacyjna modelu COM).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 W tym artykule opisano metody współpraca między kodem C# zarządzanego i kodu niezarządzanego.  
  
 [Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Zawiera opis funkcji, które zostały wprowadzone w programie Visual C# ułatwia programowanie Office.  
  
 [Instrukcje: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 W tym artykule opisano, jak używać właściwości indeksowanych do dostępu do właściwości modelu COM, które mają parametry.  
  
 [Instrukcje: użycie wywołania platformy do odtwarzania pliku Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Informacje dotyczące używania platformy wywołania usług do odtwarzania pliku dźwiękowego .wav w systemie operacyjnym Windows.  
  
 [Wskazówki: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Przedstawia sposób tworzenia skoroszytu programu Excel i dokument programu Word, zawierającą łącze do skoroszytu.  
  
 [Przykładowa klasa modelu COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Demonstracja ujawnia klasy C# jako obiekt COM.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)  
 [Wskazówki: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
