---
title: Przegląd formularzy systemu Windows i niezarządzanych aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: 1f7cfa17ce763ff84eeb052a4ea1a3a900970782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528635"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Przegląd formularzy systemu Windows i niezarządzanych aplikacji
Aplikacji formularzy systemu Windows i formantów może współdziałać z niezarządzanych aplikacji, z niektórych ostrzeżenia. W poniższych sekcjach opisano scenariusze i konfiguracje obsługujące aplikacje i formantów formularzy systemu Windows oraz te, które nie obsługują.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Formanty i aplikacji ActiveX formularzy systemu Windows  
 Z wyjątkiem programu Microsoft Internet Explorer oraz Microsoft Foundation Classes (MFC) formanty formularzy systemu Windows nie są obsługiwane w aplikacji hosta formantów ActiveX. Inne aplikacje i narzędzia deweloperskie, które są w stanie hosting formantów ActiveX kontenerów testów z wersji programu Visual Studio, które jest wcześniejsza niż Visual Studio .NET 2003, w tym nie są obsługiwane hosty dla formantów formularzy systemu Windows.  
  
 Te ograniczenia mają zastosowanie również do używania formanty formularzy systemu Windows za pośrednictwem Component Object Model COM interop. Używanie formantu formularzy systemu Windows za pośrednictwem wywoływana otoka COM (CCW) jest obsługiwana tylko w programie Internet Explorer. Aby uzyskać więcej informacji na temat Usługa międzyoperacyjna modelu COM Zobacz  
  
 [Współdziałanie z COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 W poniższej tabeli przedstawiono dostępne ActiveX hostingu obsługę formantów formularzy systemu Windows.  
  
|Wersja Windows Forms|Obsługa|  
|---------------------------|-------------|  
|.NET framework w wersji 1.0|Internet Explorer 5.01 lub nowszy|  
|.NET framework w wersji 1.1 lub nowszej|Internet Explorer 5.01 lub nowszy<br /><br /> Microsoft Foundation klas (MFC) 7.0 lub nowszym|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hosting składników formularzy systemu Windows jako formantów ActiveX  
 W .NET Framework 1.1 Obsługa została rozszerzona, aby uwzględnić MFC 7.0 i nowszych wersjach. Ta obsługa obejmuje wszystkie kontener, który jest w pełni zgodny z MFC 7.0 i nowszych kontener formantu ActiveX.  
  
 Rejestracja formantów formularzy systemu Windows jako formantów ActiveX nie jest obsługiwana. Ponadto wywołanie `com.ms.win32.Ole32.CoCreateInstance` metoda dla formantów formularzy systemu Windows nie jest obsługiwana. Obsługiwane jest tylko aktywacji zarządzanej formanty formularzy systemu Windows. Po utworzeniu formantu formularzy systemu Windows może obsługiwać go w aplikacji MFC, tak jak w przypadku formantu ActiveX.  
  
 Aby użyć formanty formularzy systemu Windows w niezarządzanej aplikacji, możesz hosta CLR za pomocą niezarządzanych hostingu interfejsów API środowiska CLR lub użyć funkcji międzyoperacyjności języka C++. Korzystanie z funkcji współdziałania C++ jest zalecanym rozwiązaniem.  
  
## <a name="windows-forms-in-com-client-applications"></a>Formularze systemu Windows w aplikacjach klienckich COM  
 Po otwarciu formularza systemu Windows z modelu COM aplikacji klienta, takich jak aplikacji Visual Basic 6.0 lub aplikacji MFC formularza może zachowywać się nieoczekiwanie. Na przykład po naciśnięciu klawisza TAB fokus nie zmienia z jednego formantu do innego formantu. Po naciśnięciu klawisza ENTER podczas przycisku polecenia ma fokus, przycisk w <xref:System.Windows.Forms.Control.Click> nie zdarzenia. Może również wystąpić nieoczekiwane zachowanie naciśnięć klawiszy lub działanie myszy.  
  
 Dzieje się tak, ponieważ niezarządzanej aplikacji nie obsługują pętli komunikatów formularzy systemu Windows wymaga, aby działać poprawnie. Pętli komunikatów udostępniany przez aplikację klienta COM jest różni się od pętli komunikatów formularzy systemu Windows.  
  
 Komunikat aplikacji pętli jest pętli wewnętrzny programu, które pobierają wiadomości z kolejki komunikatów dla wątku, tłumaczy je, a następnie wysyła je do aplikacji, które mają być obsługiwane. Pętla wiadomości dla formularza systemu Windows nie ma taką samą architekturę jako pętli komunikatów, zapewniające w starszych aplikacjach, takich jak aplikacje Visual Basic 6.0 i aplikacjach MFC. Komunikaty okna, które są wysyłane do pętli komunikatów mogą być traktowane inaczej niż oczekiwana liczba w formularzu systemu Windows. W związku z tym mogą wystąpić nieoczekiwane zachowanie. Niektórych kombinacji klawiszy mogą nie działać prawidłowo, niektóre działania myszy może nie działać lub niektóre zdarzenia nie może zostać zgłoszone, zgodnie z oczekiwaniami.  
  
## <a name="resolving-interoperability-issues"></a>Rozwiązywanie problemów ze współdziałaniem  
 Można rozwiązać te problemy przez wyświetlanie w formularzu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, który jest tworzony przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Aby poprawnie z aplikacji klienckiej COM służbowy formularza systemu Windows, należy uruchomić je na pętli komunikatów formularzy systemu Windows. Aby to zrobić, użyj jednej z następujących metod:  
  
-   Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Wyświetlania każdego formularza systemu Windows na nowym wątku. Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Formularze Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Współdziałanie COM w aplikacjach .NET Framework](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Przykłady współdziałania COM](http://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (importer kontrolki ActiveX formularzy Windows Forms)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [Udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Pakowanie zestawu dla modelu COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Rejestrowanie zestawów do użycia z modelem COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
