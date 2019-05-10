---
title: 'Instrukcje: Tworzenie prywatnej kolekcji czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 1aa3030d9daea57bb9b8970baa78f8117a07bd1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624204"
---
# <a name="how-to-create-a-private-font-collection"></a>Instrukcje: Tworzenie prywatnej kolekcji czcionek
<xref:System.Drawing.Text.PrivateFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjna klasa bazowa. Możesz użyć <xref:System.Drawing.Text.PrivateFontCollection> obiekt, aby zachować zestaw czcionki specjalnie dla twojej aplikacji. Zbieranie prywatnych czcionki mogą obejmować czcionki systemowe zainstalowane, a także czcionek, które nie zostały zainstalowane na komputerze. Aby dodać plik czcionki do kolekcji prywatnych czcionki, należy wywołać <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metody <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiekt zawiera tablicę <xref:System.Drawing.FontFamily> obiektów.  
  
 Liczbę rodzin czcionek w kolekcji czcionki prywatnych nie jest zawsze taka sama jak liczba pliki czcionek, które zostały dodane do kolekcji. Na przykład załóżmy, że pliki ArialBd.tff Times.tff i TimesBd.tff jest dodać do kolekcji. Nastąpi trzy pliki, ale tylko dwa rodziny w kolekcji, ponieważ Times.tff i TimesBd.tff należą do tej samej rodziny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje następujące pliki czcionki trzy do <xref:System.Drawing.Text.PrivateFontCollection> obiektu:  
  
- C:\\*systemroot*\Fonts\Arial.tff (Arial, regularne)  
  
- C:\\*systemroot*\Fonts\CourBI.tff (Courier New pogrubiona kursywa)  
  
- C:\\*systemroot*\Fonts\TimesBd.tff (razy nowe Roman, pogrubioną)  
  
 Ten kod pobiera tablicę <xref:System.Drawing.FontFamily> obiekty <xref:System.Drawing.Text.FontCollection.Families%2A> właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 Dla każdego <xref:System.Drawing.FontFamily> obiektu w kolekcji, kod wywołuje <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodę pozwala ustalić, czy dostępne są różne style (regularnych, pogrubienie, kursywa, pogrubienie, kursywa, podkreślenie i przekreślenie). Argumenty przekazane do <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metody są elementami członkowskimi <xref:System.Drawing.FontStyle> wyliczenia.  
  
 Jeśli połączenie danej rodziny/styl jest dostępna, <xref:System.Drawing.Font> obiekt jest konstruowany przy użyciu tej rodziny i stylu. Pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest nazwa rodziny czcionek (nie <xref:System.Drawing.FontFamily> obiektu, jak w przypadku innych zmian <xref:System.Drawing.Font.%23ctor%2A> konstruktora). Po <xref:System.Drawing.Font> obiekt jest konstruowany, zostanie on przekazany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy, aby wyświetlić nazwę rodziny, wraz z nazwą stylu.  
  
 Dane wyjściowe poniższy kod jest podobne do danych wyjściowych, pokazane na poniższej ilustracji:  
  
 ![Zrzut ekranu pokazujący tekstu w różnych czcionek.](./media/how-to-create-a-private-font-collection/various-fonts-text-output.png)  
  
 Arial.tff (który został dodany do kolekcji prywatnych czcionki w poniższym przykładzie kodu) to plik czcionka Arial stylu regularne. Należy jednak pamiętać, że dane wyjściowe programu zawiera kilka dostępnych stylów innych niż zwykłych rodziny czcionka Arial. To dlatego, że [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować pogrubienie, kursywa i pogrubiony kursywy z regularnych stylu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można utworzyć również przekreślenia z regularnych stylu i podkreśleń.  
  
 Podobnie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować styl pogrubiony kursywy, który z styl pogrubiony i kursywę stylu. Dane wyjściowe programu pokazuje italic styl pogrubiony jest dostępny dla systemów z rodziny razy, mimo że TimesBd.tff (razy nowe Roman, pogrubienie) jest tylko plik razy w kolekcji.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Text.PrivateFontCollection>
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
