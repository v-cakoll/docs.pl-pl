---
title: Jak za pomocą programowania drukować pliki XPS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: a42f9b2101266857e56dee6836f4c3b27b3c6f96
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188342"
---
# <a name="how-to-programmatically-print-xps-files"></a>Jak za pomocą programowania drukować pliki XPS
Możesz użyć jednego przeciążenia <xref:System.Printing.PrintQueue.AddJob%2A> metodę, aby wydrukować [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] plików bez otwierania <xref:System.Windows.Controls.PrintDialog> lub w zasadzie dowolnego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] na wszystkich.  
  
 Możesz również wydrukować [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] plików przy użyciu wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Aby uzyskać więcej informacji na ten temat [drukowanie dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).  
  
 Innym sposobem drukowanie [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] jest użycie <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> lub <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> metody <xref:System.Windows.Controls.PrintDialog> kontroli. Zobacz [Wywołaj okno dialogowe drukowania](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Przykład  
 Główne kroki, aby za pomocą parametru trzech <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody są następujące. W poniższym przykładzie zwraca szczegółowe informacje.  
  
1.  Określ, czy drukarka występuje XPSDrv drukarki. (Zobacz [Omówienie drukowania](printing-overview.md) więcej informacji na temat XPSDrv.)  
  
2.  Jeśli drukarka jest drukarki XPSDrv, ustawić komórka wątku pojedynczego wątku.  
  
3.  Utwórz wystąpienie serwera wydruku, a obiekt kolejki wydruku.  
  
4.  Wywołaj metodę, określając nazwę zadania, plików, które mają być drukowane i <xref:System.Boolean> flaga oznaczająca, czy drukarka jest XPSDrv.  
  
 W poniższym przykładzie pokazano, jak dzielić na partie Drukuj wszystkie [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] plików w katalogu. Mimo że aplikacja monituje użytkownika o określ katalog, parametr trzech <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metoda nie wymaga [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Może służyć w dowolnej ścieżce kodu których masz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] nazwa pliku i ścieżkę, którą można przekazać do niego.  
  
 Parametr trzech <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> przeciążenia <xref:System.Printing.PrintQueue.AddJob%2A> musi działać w komórka wątku pojedynczego zawsze wtedy, gdy <xref:System.Boolean> parametr jest `false`, który musi być, gdy jest używany bez XPSDrv drukarki. Jednakże domyślny stan apartamentu dla [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] jest wiele wątków. To ustawienie domyślne muszą zostać wycofane, ponieważ w przykładzie założono drukarek innych XPSDrv.  
  
 Istnieją dwa sposoby, aby zmienić domyślny. Jednym ze sposobów jest po prostu Dodaj <xref:System.STAThreadAttribute> (czyli "`[System.STAThreadAttribute()]`") tuż nad pierwszy wiersz aplikacji `Main` — metoda (zazwyczaj "`static void Main(string[] args)`"). Jednak wiele aplikacji wymaga `Main` metody mają stan wielowątkowej, więc ma druga metoda: wstrzymanie wywołanie <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> w oddzielnym wątku, w których stan apartamentu jest równa <xref:System.Threading.ApartmentState.STA> z <xref:System.Threading.Thread.SetApartmentState%2A>. W poniższym przykładzie użyto tej techniki drugiego.  
  
 W związku z tym przykład rozpoczyna się przez utworzenie wystąpienia <xref:System.Threading.Thread> obiektu i przekazanie do niej **PrintXPS** metodę jako <xref:System.Threading.ThreadStart> parametru. ( **PrintXPS** metoda jest zdefiniowana w tym przykładzie w dalszej części.) Następnie wątek jest równa komórka wątku pojedynczego. Kod tylko pozostałe `Main` metoda uruchamia nowy wątek.  
  
 Rodzaje przykładu znajduje się w `static` **BatchXPSPrinter.PrintXPS** metody. Po utworzeniu serwera wydruku i kolejki, metoda monituje użytkownika o katalogu zawierającego [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] plików. Po upewnieniu się, istnienie katalogu i obecności \*XPS, pliki w nim, metoda dodaje każdego takiego pliku do kolejki wydruku. W przykładzie założono, że drukarka jest bez XPSDrv, dzięki czemu możemy kończy się sukcesem `false` do ostatniego parametru <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody. Z tego powodu metody zostanie przeprowadzona Weryfikacja [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] znaczników w pliku, zanim spróbuje przekonwertować języka opisu strony drukarki. Jeśli sprawdzanie poprawności nie powiedzie się, jest zgłaszany wyjątek. Przykładowy kod będzie przechwycić wyjątek, Powiadom użytkownika o nim i przejdź do następnego przetwarzania [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pliku.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Jeśli używasz XPSDrv drukarki, a następnie można ustawić ostatni parametr `true`. W takim przypadku od [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] jest język opisu strony drukarki, metoda wyśle plik do drukarki, bez sprawdzania poprawności jej lub podczas konwertowania go do innego języka opisu strony. Jeśli wiadomo w czasie projektowania tego, czy aplikacja będzie korzystać z drukarek XPSDrv, można zmodyfikować aplikację, aby odczytywać <xref:System.Printing.PrintQueue.IsXpsDevice%2A> właściwości i gałąź, zgodnie z tego, co znajduje.  
  
 Ponieważ początkowo będą kilka drukarek XPSDrv dostępne natychmiast po wydaniu [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] i Microsoft .NET Framework, może być konieczne zamaskowania bez XPSDrv drukarki jako drukarki XPSDrv. Aby to zrobić, należy dodać do listy plików w następującym kluczu rejestru komputera z uruchomioną aplikację Pipelineconfig.xml:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter >* \DependentFiles  
  
 gdzie  *\<PseudoXPSPrinter >* jest dowolnym kolejki wydruku. Następnie należy ponownie uruchomić komputer.  
  
 Ten kamuflażu umożliwią przekazać `true` jako ostatni parametr z <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> bez powodowania wyjątek, ale ponieważ  *\<PseudoXPSPrinter >* nie jest tak naprawdę drukarki XPSDrv będzie drukować tylko wyrzucania elementów.  
  
 **Uwaga** dla uproszczenia w powyższym przykładzie użyto obecności \*rozszerzenie .xps jako jego test, który jest plikiem [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Jednak [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pliki nie mają mieć tego rozszerzenia. [IsXPS.exe (narzędzie zgodności isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) jeden ze sposobów testowania pliku dla [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ważności.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](https://www.microsoft.com/xps)  
 [Drukowanie dokumentów XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))  
 [Zarządzana i niezarządzana wątkowość](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))  
 [isXPS.exe (narzędzie zgodności isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))  
 [Dokumenty w WPF](documents-in-wpf.md)  
 [Przegląd drukowania](printing-overview.md)
