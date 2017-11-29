---
title: 'Porady: tworzenie prywatnej kolekcji czcionek'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3016fb9a1b1d8466137bcaddb0b885c02c399baf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-private-font-collection"></a>Porady: tworzenie prywatnej kolekcji czcionek
<xref:System.Drawing.Text.PrivateFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjnej klasy podstawowej. Można użyć <xref:System.Drawing.Text.PrivateFontCollection> obiektu przechowywać zestawu czcionek specjalnie dla aplikacji. Kolekcja prywatnej czcionki mogą obejmować czcionek zainstalowanego systemu, a także czcionek, które nie zostały zainstalowane na komputerze. Aby dodać plik czcionki do kolekcji czcionki prywatnych, należy wywołać <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metody <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiektu zawiera tablicę <xref:System.Drawing.FontFamily> obiektów.  
  
 Liczba rodziny czcionek w kolekcji prywatnych czcionek nie jest zawsze taka sama jak liczba plików czcionek, które zostały dodane do kolekcji. Na przykład załóżmy, że pliki ArialBd.tff, Times.tff i TimesBd.tff można dodać do kolekcji. Będzie trzy pliki, ale tylko dwa rodzin w kolekcji ponieważ Times.tff i TimesBd.tff należą do tej samej rodziny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dodano następujące pliki trzy czcionki do <xref:System.Drawing.Text.PrivateFontCollection> obiektu:  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, regularne)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Courier New pogrubienie, kursywa)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (razy nowe łacińskich, pogrubione)  
  
 Ten kod pobiera tablicę <xref:System.Drawing.FontFamily> obiektów z <xref:System.Drawing.Text.FontCollection.Families%2A> właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 Dla każdego <xref:System.Drawing.FontFamily> obiektu w kolekcji, kod wywołuje <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodę, aby określić, czy dostępne są różne style (regularne, pogrubienie, kursywa, pogrubienie, kursywa, podkreślenia i przekreślenia). Argumenty przekazywane do <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metody są elementami członkowskimi <xref:System.Drawing.FontStyle> wyliczenia.  
  
 Jeśli jest dostępna, kombinacja danej rodziny i stylu <xref:System.Drawing.Font> obiekt jest tworzony przy użyciu tej rodziny i stylu. Pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest nazwę rodziny czcionek (nie <xref:System.Drawing.FontFamily> obiektów, jak w przypadku innych zmian <xref:System.Drawing.Font.%23ctor%2A> konstruktora). Po <xref:System.Drawing.Font> konstruowania obiektu, jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy do wyświetlenia nazwisko oraz nazwę stylu.  
  
 Dane wyjściowe następujący kod jest podobny do danych wyjściowych pokazano na poniższej ilustracji.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff (który został dodany do kolekcji prywatnych czcionki w poniższym przykładzie kodu) jest plikiem czcionki Arial stylu regularne. Należy jednak pamiętać, że program dane wyjściowe zawierają dostępne style kilka innych niż zwykła dla rodziny czcionek Arial. Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować pogrubienie, kursywa i bold kursywy od zwykłego stylu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]można również utworzyć różne podkreślenia i przekreślenia od zwykłego stylu.  
  
 Podobnie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować bold styl kursywą z albo bold stylu lub kursywą. Dane wyjściowe programu zawiera styl pogrubiony kursywą jest dostępna dla systemów z rodziny razy, nawet jeśli jest to jedyny TimesBd.tff (razy nowe łacińskich, pogrubione) pliku razy w kolekcji.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
