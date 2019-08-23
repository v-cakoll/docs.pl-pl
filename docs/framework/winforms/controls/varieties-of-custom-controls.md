---
title: Różne typy formantów niestandardowych
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950095"
---
# <a name="varieties-of-custom-controls"></a>Różne typy formantów niestandardowych
Za pomocą .NET Framework można opracowywać i implementować nowe kontrolki. Można zwiększyć funkcjonalność znanego formantu użytkownika, a także istniejące kontrolki przez dziedziczenie. Możesz również pisać niestandardowe kontrolki, które wykonują własne malowanie.  
  
 Wybór rodzaju kontrolki do utworzenia może być mylący. W tym temacie przedstawiono różnice między różnymi rodzajami formantów, z których można dziedziczyć, oraz informacje na temat sposobu wybierania określonego rodzaju kontroli dla projektu.  
  
> [!NOTE]
> Aby uzyskać informacje na temat tworzenia kontrolki do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="base-control-class"></a>Podstawowa klasa kontroli  
 <xref:System.Windows.Forms.Control> Klasa jest klasą bazową dla formantów Windows Forms. Zapewnia infrastrukturę wymaganą do wyświetlania wizualizacji w aplikacjach Windows Forms.  
  
 <xref:System.Windows.Forms.Control> Klasa wykonuje następujące zadania w celu zapewnienia wyświetlania wizualizacji w aplikacjach Windows Forms:  
  
- Uwidacznia uchwyt okna.  
  
- Zarządza routingiem komunikatów.  
  
- Udostępnia zdarzenia myszy i klawiatury oraz wiele innych zdarzeń interfejsu użytkownika.  
  
- Udostępnia zaawansowane funkcje układu.  
  
- Zawiera wiele właściwości specyficznych dla wyświetlania wizualizacji, <xref:System.Windows.Forms.Control.ForeColor%2A>takich <xref:System.Windows.Forms.Control.BackColor%2A>jak <xref:System.Windows.Forms.Control.Height%2A>,, <xref:System.Windows.Forms.Control.Width%2A>, i.  
  
- Zapewnia obsługę funkcji zabezpieczeń i wątkowości, która jest niezbędna do działania formantu Windows Forms jako formantu® ActiveX programu Microsoft®.  
  
 Ze względu na to, że większość infrastruktury jest dostarczana przez klasę bazową, jest stosunkowo łatwa do opracowania własnych formantów Windows Forms.  
  
## <a name="kinds-of-controls"></a>Rodzaje kontrolek  
 Windows Forms obsługuje trzy rodzaje kontrolek zdefiniowanych przez użytkownika: *złożone*, *rozszerzone*i *niestandardowe*. W poniższych sekcjach opisano każdy rodzaj kontroli i zawarto zalecenia dotyczące wybierania rodzaju do użycia w projektach.  
  
### <a name="composite-controls"></a>Formanty złożone  
 Formant złożony jest kolekcją formantów Windows Forms hermetyzowanych w wspólnym kontenerze. Tego rodzaju kontrolka jest czasami nazywana *kontrolką użytkownika*. Zawarte kontrolki są nazywane *kontrolkami elementów*.  
  
 Kontrolka złożona zawiera wszystkie funkcje, które są skojarzone z poszczególnymi kontrolkami Windows Forms, i umożliwia selektywne Uwidacznianie i wiązanie ich właściwości. Złożona kontrolka zawiera również dużą liczbę domyślnych funkcji obsługi klawiatury bez dodatkowych nakładów programistycznych.  
  
 Na przykład można skompilować formant złożony, aby wyświetlić dane adresowe klienta z bazy danych. Ta kontrolka może zawierać <xref:System.Windows.Forms.DataGridView> kontrolkę wyświetlającą pola bazy danych <xref:System.Windows.Forms.BindingSource> , w celu obsługi powiązania ze źródłem <xref:System.Windows.Forms.BindingNavigator> danych, a także kontrolę nad rekordami. Można wybiórczo uwidocznić właściwości powiązania danych i można spakować i ponownie użyć całej kontrolki z aplikacji do aplikacji. Aby zapoznać się z przykładem tego rodzaju formantu złożonego [, zobacz How to: Zastosuj atrybuty w kontrolkach](how-to-apply-attributes-in-windows-forms-controls.md)Windows Forms.  
  
 W celu utworzenia formantu złożonego pochodnego od <xref:System.Windows.Forms.UserControl> klasy. Klasa <xref:System.Windows.Forms.UserControl> bazowa zapewnia Routing klawiatury dla formantów podrzędnych i umożliwia kontrolom podrzędnym działanie jako grupę. Aby uzyskać więcej informacji, zobacz [Tworzenie złożonego formantu Windows Forms](developing-a-composite-windows-forms-control.md).  
  
 **Zalecenie**  
  
 Dziedzicz z klasy <xref:System.Windows.Forms.UserControl> , jeśli:  
  
- Chcesz połączyć funkcje kilku Windows Forms formantów w jedną jednostkę wielokrotnego użytku.  
  
### <a name="extended-controls"></a>Formanty rozszerzone  
 Można utworzyć formant dziedziczony z dowolnej istniejącej kontrolki Windows Forms. Korzystając z tej metody, można zachować wszystkie nieodłączne funkcje formantu Windows Forms, a następnie zwiększyć tę funkcjonalność przez dodanie niestandardowych właściwości, metod lub innych funkcji. Za pomocą tej opcji można przesłonić logikę malowania formantu podstawowego, a następnie zwiększyć jej wygląd.  
  
 Na przykład można utworzyć kontrolkę pochodzącą od <xref:System.Windows.Forms.Button> kontrolki, która śledzi liczbę razy kliknięcia przez użytkownika.  
  
 W niektórych kontrolkach można również dodać niestandardowy wygląd do graficznego interfejsu użytkownika formantu przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej. W przypadku przycisku rozszerzonego, który śledzi kliknięcia, można zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby wywołać podstawową <xref:System.Windows.Forms.Control.OnPaint%2A>implementację, a następnie narysować liczbę kliknięć <xref:System.Windows.Forms.Button> w jednym rogu obszaru klienckiego kontrolki.  
  
 **Zalecenie**  
  
 Dziedzicz z kontrolki Windows Forms, jeśli:  
  
- Większość potrzebnych funkcji jest już identyczna z istniejącą kontrolką Windows Forms.  
  
- Nie potrzebujesz niestandardowego graficznego interfejsu użytkownika lub chcesz zaprojektować nowy graficzny interfejs użytkownika dla istniejącej kontrolki.  
  
### <a name="custom-controls"></a>Formanty niestandardowe  
 Innym sposobem, aby utworzyć formant, jest utworzenie go znacznie od początku przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasa zawiera wszystkie podstawowe funkcje wymagane przez kontrolki, w tym zdarzenia dotyczące myszy i klawiatury, ale nie konkretne funkcje kontroli ani interfejs graficzny.  
  
 Tworzenie kontrolki przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga znacznie większej liczby myśli i wysiłku niż dziedziczenie z <xref:System.Windows.Forms.UserControl> lub istniejącej kontrolki Windows Forms. Ze względu na to, że jest to świetna okazja do wdrożenia, formant może mieć większą elastyczność niż w przypadku kontroli złożonej lub rozszerzonej i można dostosować swój formant do swoich potrzeb.  
  
 Aby zaimplementować kontrolkę niestandardową, należy napisać kod dla <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzenia kontrolki, a także dowolny kod specyficzny dla funkcji. Możesz również zastąpić <xref:System.Windows.Forms.Control.WndProc%2A> metodę i bezpośrednio obsłużyć komunikaty systemu Windows. Jest to najbardziej wydajny sposób tworzenia kontrolek, ale aby efektywnie korzystać z tej techniki, należy zapoznać się z interfejsem API programu Microsoft Win32®.  
  
 Przykładem kontrolki niestandardowej jest kontrolka zegara, która duplikuje wygląd i zachowanie zegara analogowego. Nastąpi Odrysowanie niestandardowe, aby spowodować, że zegar zostanie przesunięty <xref:System.Windows.Forms.Timer.Tick> w odpowiedzi na zdarzenia <xref:System.Windows.Forms.Timer> z wewnętrznego składnika. Aby uzyskać więcej informacji, zobacz [jak: Opracowywanie prostej kontrolki](how-to-develop-a-simple-windows-forms-control.md)Windows Forms.  
  
 **Zalecenie**  
  
 Dziedzicz z klasy <xref:System.Windows.Forms.Control> , jeśli:  
  
- Chcesz zapewnić niestandardową reprezentację formantu.  
  
- Musisz zaimplementować niestandardowe funkcje, które nie są dostępne za poorednictwem formantów standardowych.  
  
### <a name="activex-controls"></a>Kontrolki ActiveX  
 Mimo że Windows Forms infrastruktura została zoptymalizowana pod kątem hostowania Windows Forms formantów, nadal można używać kontrolek ActiveX. To zadanie jest obsługiwane w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Dodaj kontrolki ActiveX do](how-to-add-activex-controls-to-windows-forms.md)Windows Forms.  
  
### <a name="windowless-controls"></a>Kontrolki bez okien  
 Technologie Microsoft Visual Basic® 6.0 i ActiveX obsługują kontrolki *bez okien* . Kontrolki bez okien nie są obsługiwane w Windows Forms.  
  
## <a name="custom-design-experience"></a>Niestandardowe środowisko projektowe  
 Jeśli zachodzi potrzeba zaimplementowania niestandardowego środowiska czasu projektowania, można utworzyć własnego projektanta. W przypadku kontrolek złożonych należy utworzyć niestandardową klasę <xref:System.Windows.Forms.Design.ParentControlDesigner> projektanta z <xref:System.Windows.Forms.Design.DocumentDesigner> lub klas. W przypadku kontrolek rozszerzonych i niestandardowych należy utworzyć niestandardową <xref:System.Windows.Forms.Design.ControlDesigner> klasę projektanta z klasy.  
  
 Użyj, <xref:System.ComponentModel.DesignerAttribute> aby skojarzyć swój formant z projektantem. Aby uzyskać więcej informacji, zobacz [rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) i [instrukcje: Utwórz formant Windows Forms, który korzysta z funkcji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))czasu projektowania.  
  
## <a name="see-also"></a>Zobacz także

- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Instrukcje: Opracowywanie prostej kontrolki Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Opracowywanie złożonej kontrolki formularzy Windows Forms](developing-a-composite-windows-forms-control.md)
- [Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Instrukcje: Utwórz formant Windows Forms, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
