---
title: Omówienie niezarządzanych aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: 0b4c3e738848be1ead2adeb1945e168c9db60071
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732536"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Przegląd formularzy systemu Windows i niezarządzanych aplikacji
Windows Forms aplikacje i kontrolki mogą współdziałać z niezarządzanymi aplikacjami z pewnymi zastrzeżeniami. W poniższych sekcjach opisano scenariusze i konfiguracje, które Windows Forms aplikacjami i kontrolami, oraz te, które nie są obsługiwane przez klienta.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Kontrolki Windows Forms i aplikacje ActiveX  
 Z wyjątkiem programu Microsoft Internet Explorer i Microsoft Foundation Classes (MFC), formanty Windows Forms nie są obsługiwane w aplikacjach przeznaczonych do hostowania formantów ActiveX. Inne aplikacje i narzędzia programistyczne, które mogą hostować kontrolki ActiveX, w tym kontenery testów ActiveX z wersji programu Visual Studio, które są starsze niż Visual Studio .NET 2003, nie są obsługiwane na hostach dla formantów Windows Forms.  
  
 Te ograniczenia stosują się również do korzystania z formantów Windows Forms za pomocą współdziałania Component Object Model COM. Korzystanie z kontrolki Windows Forms w ramach otoki wywoływanej przez COM (CCW) jest obsługiwane tylko w programie Internet Explorer. Aby uzyskać więcej informacji na temat międzyoperacyjności modelu COM, zobacz  
  
 [Międzyoperacyjność modelu COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 W poniższej tabeli przedstawiono dostępną obsługę ActiveX hostingu formantów Windows Forms.  
  
|Wersja Windows Forms|Obsługa|  
|---------------------------|-------------|  
|.NET Framework wersja 1,0|Internet Explorer 5,01 i nowsze wersje|  
|.NET Framework wersja 1,1 lub nowsza|Internet Explorer 5,01 i nowsze wersje<br /><br /> Microsoft Foundation Classes (MFC) 7,0 i nowsze|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hosting Windows Forms składników jako kontrolki ActiveX  
 W .NET Framework 1,1 wsparcie zostało rozszerzone w taki sposób, aby obejmowało MFC 7,0 i nowsze wersje. Ta obsługa obejmuje każdy kontener, który jest w pełni zgodny z MFC 7,0 i nowszymi kontenera formantów ActiveX.  
  
 Jednak rejestracja Windows Forms kontrolek jako kontrolki ActiveX nie jest obsługiwana. Ponadto wywoływanie metody `com.ms.win32.Ole32.CoCreateInstance` dla formantów Windows Forms nie jest obsługiwane. Obsługiwane są tylko zarządzane aktywacje formantów Windows Forms. Po utworzeniu kontrolki Windows Forms można hostować ją w aplikacji MFC podobnie jak w przypadku kontrolki ActiveX.  
  
 Aby korzystać z formantów Windows Forms w niezarządzanej aplikacji, musisz hostować środowisko CLR przy użyciu niezarządzanych interfejsów API hostingu środowiska C++ CLR lub użyć funkcji międzyoperacyjnych. Zalecanym C++ rozwiązaniem jest użycie funkcji międzyoperacyjnych.  
  
## <a name="windows-forms-in-com-client-applications"></a>Windows Forms w aplikacjach klienckich COM  
 Po otwarciu formularza systemu Windows z aplikacji klienckiej COM, takiej jak aplikacja Visual Basic 6,0 lub aplikacja MFC, formularz może zachowywać się nieoczekiwanie. Na przykład po naciśnięciu klawisza TAB fokus nie zmienia się z jednej kontrolki na inną. Po naciśnięciu klawisza ENTER, gdy przycisk polecenia ma fokus, zdarzenie <xref:System.Windows.Forms.Control.Click> przycisku nie zostanie zgłoszone. Może również wystąpić nieoczekiwane zachowanie dla naciśnięć klawiszy lub działania myszy.  
  
 Takie zachowanie występuje, ponieważ niezarządzana aplikacja nie implementuje obsługi pętli komunikatów, która Windows Forms wymaga prawidłowego działania. Pętla komunikatów dostarczana przez aplikację kliencką COM różni się zasadniczo od pętli komunikatów Windows Forms.  
  
 Pętla komunikatów aplikacji to wewnętrzna pętla programu, która pobiera komunikaty z kolejki komunikatów wątku, tłumaczy je, a następnie wysyła je do aplikacji, która ma być obsługiwana. Pętla komunikatów dla formularza systemu Windows nie ma takiej samej architektury jak pętle komunikatów, które są dostępne we wcześniejszych aplikacjach, takich jak aplikacje Visual Basic 6,0 i aplikacje MFC. Komunikaty okna, które są publikowane w pętli komunikatów mogą być obsługiwane inaczej niż oczekiwano w formularzu systemu Windows. W związku z tym może wystąpić nieoczekiwane zachowanie. Niektóre kombinacje naciśnięć klawiszy mogą nie działać, niektóre działania myszy mogą nie działać lub niektóre zdarzenia mogą nie być wywoływane zgodnie z oczekiwaniami.  
  
## <a name="resolving-interoperability-issues"></a>Rozwiązywanie problemów ze współdziałaniem  
 Te problemy można rozwiązać, wyświetlając formularz w .NET Framework pętlą komunikatów, która jest tworzona przy użyciu metody <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>.  
  
 Aby formularz systemu Windows działał prawidłowo z aplikacji klienckiej modelu COM, należy uruchomić go w pętli komunikatów Windows Forms. W tym celu należy użyć jednej z następujących metod:  
  
- Użyj metody <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>, aby wyświetlić formularz systemu Windows. Aby uzyskać więcej informacji, zobacz [How to: obsługa międzyoperacyjności modelu COM przez wyświetlanie formularza systemu Windows przy użyciu metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md).  
  
- Wyświetl Każdy formularz systemu Windows w nowym wątku. Aby uzyskać więcej informacji, zobacz [How to: obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Zobacz także

- [Formularze Windows Forms i niezarządzane aplikacje](windows-forms-and-unmanaged-applications.md)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Przykłady współdziałania modelu COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/cxcz83xf(v=vs.90))
- [Aximp.exe (importer kontrolki ActiveX formularzy Windows Forms)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)
- [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)
- [Pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md)
- [Rejestrowanie zestawów do użycia z modelem COM](../../interop/registering-assemblies-with-com.md)
- [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
