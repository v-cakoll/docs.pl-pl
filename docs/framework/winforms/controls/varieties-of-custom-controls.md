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
ms.openlocfilehash: 9883f9166007405c3f47a9a1d66a3f4c546197d0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468264"
---
# <a name="varieties-of-custom-controls"></a>Różne typy formantów niestandardowych
Za pomocą programu .NET Framework można opracowanie i wdrożenie nowych kontrolek. Możesz rozszerzyć funkcjonalność formantu użytkownika z dobrze znanych również jako istniejących kontrolek poprzez dziedziczenie. Można także napisać niestandardowe formanty, które narysowania swoje własne.  
  
 Przy wyborze rozwiązania, który rodzaj kontrolki, aby utworzyć może być mylące. W tym temacie wyróżniono różnice spośród różnych rodzajów formantów, z którego może dziedziczyć i udostępnia informacje o tym, jak wybrać określonego rodzaju formantu w projekcie.  
  
> [!NOTE]
>  Aby dowiedzieć się, jak tworzenie kontrolki do użycia w formularzach sieci Web, zobacz [tworzenia formanty serwera ASP.NET niestandardowe](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Klasy bazowej  
 <xref:System.Windows.Forms.Control> Klasa jest klasą bazową dla formantów Windows Forms. Zapewnia infrastruktury wymaganej do wizualizacji do wyświetlenia w aplikacjach Windows Forms.  
  
 <xref:System.Windows.Forms.Control> Klasa wykonuje następujące zadania w celu zapewnienia wizualizacji w aplikacjach Windows Forms do wyświetlenia:  
  
-   Przedstawia uchwyt okna.  
  
-   Zarządza routing komunikatów.  
  
-   Udostępnia myszy i zdarzeń klawiatury oraz wiele innych zdarzeń interfejsu użytkownika.  
  
-   Oferuje funkcje zaawansowane układu.  
  
-   Zawiera wiele właściwości specyficzne dla wizualizacji do wyświetlenia, takie jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, i <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Zapewnia bezpieczeństwo i obsługa wątkowości niezbędne dla formantu Windows Forms jako formant ActiveX Microsoft®.  
  
 Ponieważ tak wiele infrastruktury jest dostarczany przez klasę bazową, jest stosunkowo łatwa do opracowywania własnych kontrolek Windows Forms.  
  
## <a name="kinds-of-controls"></a>Rodzaje formantów  
 Formularze Windows obsługuje trzy typy kontrolek użytkownika: *złożonego*, *rozszerzonej*, i *niestandardowe*. W poniższych sekcjach opisano każdy rodzaj kontrolki i podać zalecenia dotyczące wybierania typu do użycia w swoich projektach.  
  
### <a name="composite-controls"></a>Formanty złożone  
 Kontrolki złożonej to zbiór kontrolek Windows Forms w wspólnym kontenerem. Ten rodzaj kontroli jest czasami nazywane *kontrolki użytkownika*. Zawartych w nim formantów są nazywane *formanty składników*.  
  
 Kontrolki złożonej zawiera wszystkie funkcje nieprzerwaną pracę związany z każdą z zawartych w nim formantów Windows Forms i umożliwia selektywne udostępnianie i wiązania ich właściwości. Kontrolki złożonej także dużym stopniem domyślnie za pomocą klawiatury funkcji z nie dodatkowe postanowiło ze strony użytkownika.  
  
 Na przykład kontrolek złożonych można przystosować do wyświetlania danych adres klienta z bazy danych. Ten formant może obejmować <xref:System.Windows.Forms.DataGridView> sterowania do wyświetlania pól bazy danych <xref:System.Windows.Forms.BindingSource> do obsługi powiązania ze źródłem danych i <xref:System.Windows.Forms.BindingNavigator> kontrolki przechodzenia między rekordami. Można selektywnie ujawnić właściwości powiązań danych i może spakować i ponownie użyć kontrolki całego od aplikacji. Na przykład tego typu złożonego formantu zobacz [porady: stosowanie atrybutów w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Tworzenie kontrolki złożonej, pochodzi od <xref:System.Windows.Forms.UserControl> klasy. <xref:System.Windows.Forms.UserControl> Klasy bazowej zapewnia routing klawiatury dla podrzędnych kontrolki i umożliwia formanty podrzędne do działania w formie grupy. Aby uzyskać więcej informacji, zobacz [opracowywanie złożonej kontrolki formularzy Windows](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Zalecenie**  
  
 Dziedzicz <xref:System.Windows.Forms.UserControl> klasy, jeśli:  
  
-   Chcesz połączyć funkcje kilka kontrolek Windows Forms w pojedynczą jednostkę wielokrotnego użytku.  
  
### <a name="extended-controls"></a>Formanty rozszerzone  
 Odziedziczoną kontrolkę może pochodzić z dowolnego istniejącego formantu Windows Forms. W tym podejściu zachowania wszystkich funkcji nieprzerwaną pracę formantu Windows Forms i następnie rozszerzyć tę funkcję, dodając niestandardowe właściwości, metody lub innych funkcji. Po wybraniu tej opcji można zastąpić logikę malowania kontroli podstawowej i następnie rozszerzyć interfejs użytkownika, zmieniając jego wygląd.  
  
 Na przykład można utworzyć formant pochodzące z <xref:System.Windows.Forms.Button> formant, który śledzi, ile razy użytkownik kliknął go.  
  
 W niektórych kontrolek, można również dodać niestandardowe wygląd graficznego interfejsu użytkownika kontrolki przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej. Dla rozszerzonego przycisku, umożliwiający śledzenie kliknięć, możesz zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby wywoływać implementację podstawową <xref:System.Windows.Forms.Control.OnPaint%2A>, a następnie narysuj kliknij liczbę w jeden z rogów <xref:System.Windows.Forms.Button> obszaru klienckiego kontrolki.  
  
 **Zalecenie**  
  
 Dziedziczenie z kontrolki formularzy Windows Forms, jeśli:  
  
-   Większość funkcji, których potrzebujesz już jest identyczna z istniejącej kontrolki Windows Forms.  
  
-   Nie ma potrzeby niestandardowych graficznego interfejsu użytkownika lub projektowania nowy graficzny interfejs użytkownika do istniejącego formantu.  
  
### <a name="custom-controls"></a>Formanty niestandardowe  
 Innym sposobem, aby utworzyć formant jest utworzenie jednego z początku przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasy zawiera wszystkie podstawowe funkcje wymagane przez formanty, mysz i klawiatura, obsługa zdarzeń, w tym, ale funkcje specyficzne dla formantu lub interfejsu graficznego.  
  
 Tworzenie formantu przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga znacznie więcej myślenia i nakładu pracy niż dziedziczenie z <xref:System.Windows.Forms.UserControl> lub istniejącej kontrolki Windows Forms. Ponieważ implementację stopniem pozostanie dla Ciebie, formant może mieć większą elastyczność niż formantu złożonego lub rozszerzone i dostosować kontrolki do własnych potrzeb dokładne.  
  
 Aby zaimplementować formant niestandardowy, należy napisać kod dla <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzenia kontroli, jak również żadnego kodu właściwe dla funkcji, potrzebujesz. Możesz również zastąpić <xref:System.Windows.Forms.Control.WndProc%2A> metody i obsługują komunikaty systemu windows bezpośrednio. Jest to najbardziej wydajnymi procesorami sposób, aby utworzyć kontrolkę, ale aby efektywnie korzystać z tej techniki, należy zapoznać się z Microsoft Win32 API®.  
  
 Przykład formantu niestandardowego jest formantem zegara powielającą wygląd i zachowanie zegar analogowy. Malowanie niestandardowych jest wywoływane w celu spowodować ręce zegar przenoszone w odpowiedzi na <xref:System.Windows.Forms.Timer.Tick> zdarzenia z wewnętrznego <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego formantu formularzy Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Zalecenie**  
  
 Dziedzicz <xref:System.Windows.Forms.Control> klasy, jeśli:  
  
-   Chcesz zapewnić niestandardowy graficzną reprezentację kontrolki.  
  
-   Musisz zaimplementować niestandardowy funkcji, która nie jest dostępna za pośrednictwem standardowych kontrolek.  
  
### <a name="activex-controls"></a>Kontrolki ActiveX  
 Mimo że infrastruktura formularzy Windows została zoptymalizowana do kontrolek Windows Forms hosta, ale nadal używać kontrolki ActiveX. Są obsługiwane dla tego zadania w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie kontrolek ActiveX do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Od kontrolek bez okien  
 Obsługa technologii ActiveX the Microsoft Visual Basic® 6.0and *niepowiązanej z oknami* kontrolki. Od kontrolek bez okien nie są obsługiwane w formularzach Windows Forms.  
  
## <a name="custom-design-experience"></a>W obsłudze środowisku projektowania niestandardowego  
 Jeśli musisz zaimplementować niestandardowy środowiska czasu projektowania można tworzyć własne projektanta. W przypadku złożonych kontrolek pochodną klasę niestandardową projektanta z <xref:System.Windows.Forms.Design.ParentControlDesigner> lub <xref:System.Windows.Forms.Design.DocumentDesigner> klasy. W przypadku rozszerzonego i niestandardowych kontrolek pochodzić projektanta klasę niestandardową z <xref:System.Windows.Forms.Design.ControlDesigner> klasy.  
  
 Użyj <xref:System.ComponentModel.DesignerAttribute> do powiązania kontrolki z projektanta. Aby uzyskać więcej informacji, zobacz [rozszerzenie obsługi w czasie projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) i [porady: tworzenie Windows Forms kontroli, przyjmuje korzystać z funkcje czasu projektowania](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Instrukcje: opracowywanie prostej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Opracowywanie złożonej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Rozszerzenie obsługi w czasie projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Porady: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
