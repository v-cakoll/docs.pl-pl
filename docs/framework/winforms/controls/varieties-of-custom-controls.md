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
ms.openlocfilehash: f35fdb0f82370ed3e40aeeda01b3c88f0a8c5ec0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541232"
---
# <a name="varieties-of-custom-controls"></a>Różne typy formantów niestandardowych
Z programu .NET Framework mogą tworzyć i wdrożyć nowe kontrolki. Można rozszerzyć funkcjonalność kontrolki użytkownika znanych także jako istniejących formantów przez dziedziczenie. Można również napisać formantów niestandardowych, które własnych narysowania.  
  
 Przy wyborze, jakiego rodzaju formantu, aby utworzyć może być mylące. W tym temacie omówiono różnice między różne rodzaje formantów, z którego może dziedziczyć i dostarcza informacji o wybieraniu określonego typu formantu w projekcie.  
  
> [!NOTE]
>  Aby uzyskać informacji o tworzeniu formant do użycia w formularzach sieci Web, zobacz [tworzenia kontrolek serwera ASP.NET niestandardowe](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Klasa podstawowa sterowania  
 <xref:System.Windows.Forms.Control> Klasa jest klasą bazową dla formantów formularzy systemu Windows. Zapewnia infrastruktury wymaganej do wyświetlania w aplikacji formularzy systemu Windows.  
  
 <xref:System.Windows.Forms.Control> Klasa wykonuje następujące zadania w celu zapewnienia wyświetlania w aplikacji formularzy systemu Windows:  
  
-   Przedstawia uchwytu okna.  
  
-   Zarządza rozsyłania wiadomości.  
  
-   Zapewnia zdarzenia klawiatury i myszy oraz wiele innych zdarzeń interfejsu użytkownika.  
  
-   Udostępnia funkcje zaawansowane układu.  
  
-   Zawiera wiele właściwości specyficzne dla wyświetlania, takie jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, i <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Zapewnia bezpieczeństwo i obsługa wątkowości niezbędne dla formantu formularzy systemu Windows do działania jako formant ActiveX Microsoft®.  
  
 Ponieważ duża część infrastruktury jest dostarczany przez klasę podstawową, jest stosunkowo łatwa do opracowywania własnych formanty formularzy systemu Windows.  
  
## <a name="kinds-of-controls"></a>Typy formantów  
 Formularze systemu Windows obsługuje trzy rodzaje kontrolki użytkownika: *złożonego*, *rozszerzonej*, i *niestandardowych*. W poniższych sekcjach opisano każdy rodzaj kontroli i nadaj zalecenia dotyczące wybierania rodzaj do użycia w projektach.  
  
### <a name="composite-controls"></a>Formanty złożone  
 Formantu złożonego jest kolekcją hermetyzowane w wspólnego kontenera formantów formularzy systemu Windows. Tego rodzaju kontroli jest czasami nazywany *kontrolki użytkownika*. Formanty zawarte są nazywane *formanty składników*.  
  
 Formantu złożonego zawiera wszystkie funkcje dostępu do właściwych skojarzone z poszczególnymi zawartych w niej formanty formularzy systemu Windows i umożliwia selektywne ujawnia i powiąż ich właściwości. Formantu złożonego za zapewnia także dużą domyślnie za pomocą klawiatury funkcje z nie dodatkowych nakład pracy ze strony użytkownika.  
  
 Na przykład formantu złożonego mogą być zbudowane do wyświetlania danych adresów klienta z bazy danych. Ten formant może obejmować <xref:System.Windows.Forms.DataGridView> formantu, aby wyświetlić pola bazy danych, <xref:System.Windows.Forms.BindingSource> do obsługi powiązania ze źródłem danych, a <xref:System.Windows.Forms.BindingNavigator> formantu, aby przechodzić. Można selektywnie ujawnić właściwości powiązań danych, a można spakować i ponowne użycie kontroli całego od aplikacji. Na przykład tego rodzaju formantu złożonego zobacz [porady: zastosowanie atrybutów w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Do tworzenia złożonych kontrolek, pochodzi z <xref:System.Windows.Forms.UserControl> klasy. <xref:System.Windows.Forms.UserControl> Klasy podstawowej zapewnia routing klawiatury podrzędne kontrolki i umożliwia formantów podrzędnych z działa jako grupa. Aby uzyskać więcej informacji, zobacz [opracowywanie złożonego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Zalecenia**  
  
 Dziedzicz <xref:System.Windows.Forms.UserControl> klasy, jeśli:  
  
-   Chcesz połączyć funkcji kilku formantów formularzy systemu Windows w pojedynczą jednostkę wielokrotnego użytku.  
  
### <a name="extended-controls"></a>Formanty rozszerzone  
 Formant dziedziczony może pochodzić od dowolnego istniejącego formantu formularzy systemu Windows. Z tej metody można zachować wszystkie funkcje związane z formantu formularzy systemu Windows, a następnie rozszerzają te funkcje, dodając niestandardowe właściwości, metody lub innych funkcji. Po wybraniu tej opcji można zastąpić logiki malowanie kontrolki podstawowej i następnie rozszerzają jego interfejs użytkownika przez zmianę jego wyglądu.  
  
 Na przykład można utworzyć formantu pochodną <xref:System.Windows.Forms.Button> formant, który śledzi, ile razy użytkownik kliknął przycisk go.  
  
 W niektórych formantów można również dodać niestandardowe wygląd graficznego interfejsu użytkownika formantu przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej. Dla przycisku rozszerzonej śledzący kliknięć, można zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę do wywołania Podstawowa implementacja <xref:System.Windows.Forms.Control.OnPaint%2A>, a następnie narysuj liczba kliknij w jednym narożniku <xref:System.Windows.Forms.Button> obszaru klienckiego formantu.  
  
 **Zalecenia**  
  
 Dziedziczenie z formantu formularzy systemu Windows, jeśli:  
  
-   Większość funkcji, które są potrzebne już jest identyczny z istniejącego formantu formularzy systemu Windows.  
  
-   Nie trzeba niestandardowego graficznego interfejsu użytkownika lub projektowania nowego graficznego interfejsu użytkownika dla istniejącego formantu.  
  
### <a name="custom-controls"></a>Formanty niestandardowe  
 Innym sposobem tworzenia formantu jest utworzenie jednego z początku przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasa udostępnia wszystkie podstawowe funkcje wymagane przez funkcje kontroli, łącznie z myszy i klawiatury obsługi zdarzeń, ale nie funkcje sterowania lub interfejsu graficznego.  
  
 Tworzenie formantu przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga dużo więcej myśl i nakładu pracy niż dziedziczenie z <xref:System.Windows.Forms.UserControl> lub formant formularzy systemu Windows. Ponieważ wiele implementacji pozostanie dla Ciebie, formantu może mieć większą elastyczność niż formantu złożonego lub rozszerzone i można dostosować zgodnie z potrzebami dokładną kontrolę.  
  
 Aby zaimplementować kontrolkę niestandardową, należy napisać kod <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzeń formantu, jak również żadnego kodu właściwych dla funkcji należy. Możesz też przesłonić <xref:System.Windows.Forms.Control.WndProc%2A> metody i obsługi komunikatów systemu windows bezpośrednio. Jest to najbardziej wydajny sposób można utworzyć formantu, ale aby skutecznie użyć tej metody, należy zapoznać się z interfejsu API Microsoft Win32®.  
  
 Przykładem formant niestandardowy jest formant zegara, który stanowi duplikat wygląd i zachowanie zegar analogowy. Niestandardowe rysowania jest wywoływane w celu spowodować ręce zegara, aby przenieść w odpowiedzi na <xref:System.Windows.Forms.Timer.Tick> zdarzenia z wewnętrznego <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji, zobacz [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Zalecenia**  
  
 Dziedzicz <xref:System.Windows.Forms.Control> klasy, jeśli:  
  
-   Chcesz podać niestandardowy graficzną reprezentację formantu.  
  
-   Należy wdrożyć funkcji niestandardowych, który nie jest dostępny za pośrednictwem standardowych kontrolek.  
  
### <a name="activex-controls"></a>Kontrolki ActiveX  
 Mimo że infrastruktury formularzy systemu Windows została zoptymalizowana do hosta formanty formularzy systemu Windows, można nadal używać formantów ActiveX. Brak obsługi dla tego zadania w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów ActiveX do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Formanty bez okien  
 Obsługa technologii ActiveX the Microsoft Visual Basic® 6.0and *bez okien* kontrolki. Formanty niepowiązane z oknami nie są obsługiwane w formularzach systemu Windows.  
  
## <a name="custom-design-experience"></a>Środowisko projektowania niestandardowego  
 Jeśli musisz wdrożyć niestandardowe środowisko czasu projektowania, można tworzyć własne projektanta. W przypadku złożonych kontrolek pochodzi z niestandardowej klasy projektanta <xref:System.Windows.Forms.Design.ParentControlDesigner> lub <xref:System.Windows.Forms.Design.DocumentDesigner> klasy. Rozszerzone i niestandardowych formantów, pochodzi z niestandardowej klasy projektanta <xref:System.Windows.Forms.Design.ControlDesigner> klasy.  
  
 Użyj <xref:System.ComponentModel.DesignerAttribute> do skojarzenia z z projektantem formantu. Aby uzyskać więcej informacji, zobacz [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) i [porady: Tworzenie funkcji systemu Windows formularze kontroli czy ma korzystać z czasu projektowania](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Instrukcje: opracowywanie prostej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Opracowywanie złożonej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
