---
title: Jak za pomocą programowania drukować pliki XPS
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55a9a50527df0605cb9699622a165147597a500a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-xps-files"></a>Jak za pomocą programowania drukować pliki XPS
Można użyć jednego przeciążenia <xref:System.Printing.PrintQueue.AddJob%2A> metody do drukowania [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] pliki bez otwierania <xref:System.Windows.Controls.PrintDialog> lub zasadniczo żadnych [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] w ogóle.  
  
 Pozwala również na drukowanie [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] plików za pomocą wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Aby uzyskać więcej informacji o tym [drukowanie dokumentów XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90)).  
  
 Innym sposobem drukowanie [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] jest użycie <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> lub <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> metody <xref:System.Windows.Controls.PrintDialog> formantu. Zobacz [Wywołaj okno dialogowe drukowania](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Przykład  
 Za pomocą parametru trzech głównych kroków <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody są następujące. Poniższy przykład przedstawia szczegóły.  
  
1.  Ustal, czy drukarka jest XPSDrv. (Zobacz [Omówienie drukowania](printing-overview.md) więcej informacji o XPSDrv.)  
  
2.  Jeśli drukarka nie jest XPSDrv drukarki, ustawić apartamencie wątku pojedynczego wątku.  
  
3.  Utwórz wystąpienie serwera wydruku i obiekt kolejki wydruku.  
  
4.  Wywołaj metodę, określając nazwę zadania, plików, które mają być drukowane i <xref:System.Boolean> flaga oznaczająca, czy drukarka jest XPSDrv.  
  
 W poniższym przykładzie pokazano, jak partii drukowania wszystkich [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pliki w katalogu. Mimo że aplikacja wyświetli monit o określ katalog, parametr trzech <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metoda nie wymaga [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Można w dowolnej ścieżce kodu, gdzie masz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] nazwa pliku i ścieżki, które można przekazać do niego.  
  
 Parametr trzech <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> przeciążenia z <xref:System.Printing.PrintQueue.AddJob%2A> muszą działać w apartamencie wątku pojedynczego zawsze, gdy <xref:System.Boolean> jest parametr `false`, który musi być, gdy jest używany z systemem innym niż XPSDrv drukarki. Jednakże domyślny stan apartamentu dla [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] jest wiele wątków. To ustawienie domyślne musi być wycofana, ponieważ w przykładzie założono drukarki z systemem innym niż XPSDrv.  
  
 Istnieją dwa sposoby, aby zmienić domyślny. Jednym ze sposobów jest po prostu Dodaj <xref:System.STAThreadAttribute> (to znaczy "`[System.STAThreadAttribute()]`") powyżej pierwszy wiersz aplikacji `Main` — metoda (zazwyczaj "`static void Main(string[] args)`"). Jednak wiele aplikacji wymaga, aby `Main` metody mają stan wielowątkowej, dlatego druga metoda: Umieść wywołanie <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> w oddzielnym wątku, w których stanu apartamentu ma ustawioną wartość <xref:System.Threading.ApartmentState.STA> z <xref:System.Threading.Thread.SetApartmentState%2A>. W poniższym przykładzie użyto ta technika drugiego.  
  
 W związku z tym przykład rozpoczyna się przez utworzenie wystąpienia <xref:System.Threading.Thread> obiekt i przekazanie jej **PrintXPS** metodę jako <xref:System.Threading.ThreadStart> parametru. ( **PrintXPS** metoda jest zdefiniowana później w przykładzie.) Następny wątek ustawiono komórka wątku pojedynczego. Tylko kod pozostałych `Main` metoda uruchamia nowego wątku.  
  
 Rodzaje przykładu znajduje się w `static` **BatchXPSPrinter.PrintXPS** metody. Po utworzeniu serwera wydruku i kolejki, metoda wyświetla monit o nadrzędnym katalogu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] plików. Po sprawdzenie istnienia katalogu i w obecności \*XPS pliki w nim, metoda dodaje każdy z tych plików do kolejki wydruku. W przykładzie założono, że drukarka jest z systemem innym niż XPSDrv, dlatego firma Microsoft przekazywane `false` do ostatniego parametru metody <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody. Z tego powodu będzie sprawdzać poprawność metody [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] znacznika w pliku przed próbuje przekonwertować go do języka opisu strony drukarki. W przypadku niepowodzenia weryfikacji, jest zwracany wyjątek. Przykładowy kod będzie catch wyjątku, powiadomienie użytkownika o nim i przejdź do następnego przetwarzania [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pliku.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Jeśli używasz XPSDrv drukarki, a następnie można ustawić ostatni parametr `true`. W takim przypadku od [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] jest języka opisu strony drukarki, metoda wyśle plik do drukarki bez jej skuteczność lub konwertowana na inny język opisu strony. Aby dowiedzieć się w czasie projektowania, czy będzie używana aplikacja XPSDrv drukarki, można zmodyfikować aplikacji, aby go przeczytać <xref:System.Printing.PrintQueue.IsXpsDevice%2A> właściwości i gałęzi zgodnie z ich znalezienia.  
  
 Ponieważ początkowo będzie kilka drukarek XPSDrv dostępna natychmiast po wydaniu [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] i [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], konieczne może być ukryć drukarki z systemem innym niż XPSDrv jako XPSDrv drukarki. Aby to zrobić, należy dodać do listy plików w następującym kluczu rejestru komputera z uruchomionym aplikacji Pipelineconfig.xml:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter >*\DependentFiles  
  
 gdzie  *\<PseudoXPSPrinter >* jest wszystkie kolejki wydruku. Następnie należy ponownie uruchomić komputer.  
  
 Ten kamuflażu umożliwi przekazać `true` jako ostatni parametr z <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> bez powodowania wyjątek, ale ponieważ  *\<PseudoXPSPrinter >* nie jest drukarki XPSDrv będzie drukować tylko odzyskiwanie.  
  
 **Uwaga** dla uproszczenia w powyższym przykładzie używa obecności \*rozszerzenia XPS jako jego test, który jest plikiem [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Jednak [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pliki muszą mieć rozszerzenie. [IsXPS.exe (narzędzie zgodności isXPS)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100)) jest jednym ze sposobów testowania pliku dla [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ważności.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [Drukowanie dokumentów XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90))  
 [Zarządzana i niezarządzana wątkowość](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [isXPS.exe (narzędzie zgodności isXPS)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100))  
 [Dokumenty w WPF](documents-in-wpf.md)  
 [Przegląd drukowania](printing-overview.md)
