---
title: "Zalecenia dotyczące typu formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 638a439a663925be6eea230984310f7b86b81030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="control-type-recommendations"></a>Zalecenia dotyczące typu formantu
.NET Framework zapewnia zasilania opracowanie i wdrożenie nowych formantów. Oprócz kontroli znanych użytkowników można będzie teraz okazać, że możliwość zapisywania Kontrolki niestandardowe własnych narysowania, a nawet mogą rozszerzyć funkcjonalność dysponujące przez dziedziczenie. Przy wyborze typu formantu, aby utworzyć może być mylące. W tej sekcji przedstawiono różnice między różnymi rodzajami formantów, z którego może dziedziczyć i zapewnia uwagi dotyczące typu do wyboru dla projektu.  
  
> [!NOTE]
>  Jeśli chcesz tworzyć formantu do używania w formularzach sieci Web, zobacz [tworzenia kontrolek serwera ASP.NET niestandardowe](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Dziedziczenie z systemu Windows formantu formularzy  
 Formant dziedziczony może pochodzić od dowolnego istniejącego formantu formularzy systemu Windows. Takie podejście pozwala zachować wszystkie funkcje związane z formantu formularzy systemu Windows i następnie rozszerzają te funkcje, dodając niestandardowe właściwości, metody lub innych funkcji. Na przykład można utworzyć formantu pochodną <xref:System.Windows.Forms.TextBox> czy może akceptować tylko liczby i automatycznie konwertuje dane wejściowe na wartość. Taki formant może zawierać kod weryfikacji, który była wywoływana, gdy tekst w polu tekstowym zmienione i może mieć dodatkowe właściwości wartości. W niektórych formantów można również dodać niestandardowe wygląd do interfejsu graficznego formantu przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej.  
  
 Dziedziczenie z formantu formularzy systemu Windows, jeśli:  
  
-   Większość funkcji, które są potrzebne już jest identyczny z istniejącego formantu formularzy systemu Windows.  
  
-   Nie trzeba niestandardowego interfejsu graficznego lub projektowania nowy graficzny fronton istniejącego formantu.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Dziedziczenie z klasy UserControl  
 Kontrolka użytkownika jest zbiorem hermetyzowany do wspólnego kontenera formantów formularzy systemu Windows. Kontener zawiera wszystkie funkcje dostępu do właściwych skojarzone z poszczególnymi formanty formularzy systemu Windows i umożliwia selektywne ujawnia i powiązać ich właściwości. Przykład kontrolkę użytkownika może być utworzone w celu wyświetlenia danych adresów klienta z bazy danych formantu. Ten formant obejmuje kilka pól tekstowych do wyświetlania każdego pola i formanty przycisków poruszać się po rekordy. Selektywnie widoczne właściwości powiązania danych, a cały kontroli może być spakowany i pochodzącym z aplikacji do aplikacji.  
  
 Dziedzicz <xref:System.Windows.Forms.UserControl> klasy, jeśli:  
  
-   Chcesz połączyć funkcji kilku formantów formularzy systemu Windows w pojedynczą jednostkę wielokrotnego użytku.  
  
## <a name="inheriting-from-the-control-class"></a>Dziedziczenie z klasy formantów  
 Innym sposobem tworzenia formantu jest utworzenie znacznie od początku przez dziedziczenie z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Klasa udostępnia wszystkie podstawowe funkcje wymagane przez formanty (na przykład zdarzeń), ale nie funkcje kontroli lub interfejsu graficznego. Tworzenie formantu przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga znacznie większą myśl i nakładu niż dziedziczenie z formantu użytkownika lub formant formularzy systemu Windows. Autor napisać kod <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzeń formantu, a także kodu określonych funkcji, który jest potrzebny. Większa elastyczność jest dozwolone, jednak i możesz dostosować niestandardowych kontroli zgodnie z potrzebami dokładne. Przykładem formant niestandardowy jest formant zegara, który stanowi duplikat wygląd i działanie zegar analogowy. Niestandardowe malowania będzie można wywołać spowodować ręce zegara, aby przenieść w odpowiedzi na <xref:System.Windows.Forms.Timer.Tick> zdarzenia z wewnętrznego timer — składnik.  
  
 Dziedzicz <xref:System.Windows.Forms.Control> klasy, jeśli:  
  
-   Chcesz podać niestandardowy graficzną reprezentację formantu.  
  
-   Należy wdrożyć funkcji niestandardowych, który nie jest dostępny za pośrednictwem standardowych kontrolek.  
  
-   [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Przewodnik: serializowanie kolekcji standardowych typów za pomocą elementu DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](http://msdn.microsoft.com/en-us/library/5h0k2e6x\(v=vs.110\))  
  
-   [Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Instrukcje: dziedziczenie z klasy kontrolek](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Instrukcje: dziedziczenie z klasy UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Instrukcje: tworzenie kontrolek złożonych](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#](http://msdn.microsoft.com/en-us/library/a6h7e207\(v=vs.110\))  
  
-   [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: opracowywanie prostej kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
