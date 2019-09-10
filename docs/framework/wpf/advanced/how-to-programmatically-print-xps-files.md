---
title: 'Instrukcje: Programowe drukowanie plików XPS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 28197b22b379b84c34e7fdf8991472e082c8cb42
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855744"
---
# <a name="how-to-programmatically-print-xps-files"></a>Instrukcje: Programowe drukowanie plików XPS

Można użyć jednego przeciążenia <xref:System.Printing.PrintQueue.AddJob%2A> metody do drukowania plików XPS (XML Paper Specification) bez konieczności <xref:System.Windows.Controls.PrintDialog> otwierania lub [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , w zasadzie, w ogóle.

Możesz również wydrukować pliki XPS przy użyciu wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> metod i. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType> Aby uzyskać więcej informacji, zobacz [Drukowanie dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

Innym sposobem drukowania plików XPS jest użycie <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> metod lub. <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType> Zobacz [Wywołaj okno dialogowe drukowania](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Przykład

Główne kroki do korzystania z trzech parametrów <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> są następujące. W poniższym przykładzie przedstawiono szczegóły.

1. Ustal, czy drukarka jest drukarką XPSDrv. (Zobacz [Omówienie drukowania](printing-overview.md) , aby uzyskać więcej informacji na temat XPsDrv).

2. Jeśli drukarka nie jest drukarką XPSDrv, Ustaw element Apartment wątku na pojedynczy wątek.

3. Tworzenie wystąpienia serwera wydruku i obiektu kolejki wydruku.

4. Wywołaj metodę, określając nazwę zadania, plik do wydrukowania i <xref:System.Boolean> flagę wskazującą, czy drukarka jest drukarką XPsDrv.

W poniższym przykładzie przedstawiono sposób tworzenia wsadowego drukowania wszystkich plików XPS w katalogu. Mimo że aplikacja monituje użytkownika o określenie katalogu, Metoda trzech parametrów <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> nie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]wymaga. Może być używana w dowolnej ścieżce kodu, w której znajduje się nazwa pliku XPS i ścieżka, którą można przekazać do niego.

Przeciążenie trzech parametrów <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> <xref:System.Boolean> musi działać w jednym wątku Apartment za każdym razem, gdy parametr ma `false`wartość, co musi być używane w przypadku używania drukarki innej niż XPsDrv. <xref:System.Printing.PrintQueue.AddJob%2A> Jednak domyślny stan apartamentu dla platformy .NET to wiele wątków. Ta wartość domyślna musi być odwrócona, ponieważ w przykładzie założono, że drukarka nie XPSDrv.

Istnieją dwa sposoby zmiany domyślnego. Jednym ze sposobów jest po prostu dodanie <xref:System.STAThreadAttribute> (czyli "`[System.STAThreadAttribute()]`") tuż powyżej pierwszego `Main` wiersza metody aplikacji (zazwyczaj "`static void Main(string[] args)`"). `Main` Jednak wiele aplikacji wymaga, aby Metoda miała wielowątkowy stan Apartment, więc istnieje druga metoda: należy umieścić <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> wywołanie w osobnym wątku, którego <xref:System.Threading.Thread.SetApartmentState%2A>stan apartamentu jest ustawiony na <xref:System.Threading.ApartmentState.STA> wartość. W poniższym przykładzie zastosowano tę drugą technikę.

W związku z tym przykład zaczyna się od wystąpienia <xref:System.Threading.Thread> obiektu i przekazanie go do metody **PrintXPS** jako <xref:System.Threading.ThreadStart> parametru. (Metoda **PrintXPS** jest zdefiniowana w dalszej części tego przykładu). Następny wątek jest ustawiony na jeden apartament wątku. Jedyny pozostały kod `Main` metody uruchamia nowy wątek.

Mięso przykładu znajduje się w `static`metodzie **BatchXPSPrinter. PrintXPS** . Po utworzeniu serwera wydruku i kolejki, Metoda wyświetli użytkownikowi komunikat o katalogu zawierającym pliki XPS. Po zweryfikowaniu istnienia katalogu i obecności \*w nim plików XPS Metoda dodaje każdy plik do kolejki wydruku. W przykładzie założono, że drukarka nie jest XPsDrv, więc przekazujemy `false` do ostatniego <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parametru metody. Z tego powodu metoda sprawdzi poprawność znacznika XPS w pliku przed próbą jego przekonwertowania na język opisu strony drukarki. Jeśli weryfikacja nie powiedzie się, zostanie zgłoszony wyjątek. Przykładowy kod będzie przechwytywać wyjątek, powiadom użytkownika o nim, a następnie przejdź do, aby przetworzyć następny plik XPS.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Jeśli używasz drukarki XPSDrv, możesz ustawić końcowy parametr na `true`. W takim przypadku, ponieważ XPS to język opisu strony drukarki, Metoda wyśle plik do drukarki bez sprawdzania poprawności lub konwertowania go na inny język opisu strony. Jeśli nie jest to konieczne w czasie projektowania, niezależnie od tego, czy aplikacja będzie korzystać z drukarki XPsDrv, można zmodyfikować aplikację tak, aby odczytała <xref:System.Printing.PrintQueue.IsXpsDevice%2A> Właściwość i gałąź zgodnie z znalezionymi w tym miejscu.

Ponieważ początkowo będzie dostępnych kilka XPsDrv drukarek bezpośrednio po wydaniu programu [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] i Microsoft .NET Framework, może być konieczne przeniesienie drukarki innej niż XPsDrv jako drukarki XPsDrv. Aby to zrobić, Dodaj plik Pipelineconfig. XML do listy plików w następującym kluczu rejestru komputera, na którym działa aplikacja:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles

*gdzie\<PseudoXPSPrinter >* jest dowolną kolejką wydruku. Należy ponownie uruchomić maszynę.

Ta wartość przekazana umożliwi przekazanie `true` jako końcowy parametr programu <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> bez powodowania wyjątku, ale ponieważ  *\<PseudoXPSPrinter >* nie jest w rzeczywistości drukarką XPsDrv, drukowanie będzie miało tylko elementy bezużyteczne.

> [!NOTE]
> Dla uproszczenia w powyższym przykładzie użyto obecności \*rozszerzenia. XPS jako testu, że plik jest XPS. Jednak pliki XPS nie muszą mieć tego rozszerzenia. [IsXPS. exe (isXPS zgodność)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) to jeden z metod testowania pliku pod kątem ważności w formacie XPS.

## <a name="see-also"></a>Zobacz także

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Drukowanie dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Wątki zarządzane i niezarządzane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS. exe (Narzędzie isXPS zgodność)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
