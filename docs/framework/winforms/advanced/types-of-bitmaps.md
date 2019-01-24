---
title: Typy map bitowych
ms.date: 03/30/2017
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
ms.openlocfilehash: 3083c075bfbbd21a26f7442f9bbccbe800d73cf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674771"
---
# <a name="types-of-bitmaps"></a>Typy map bitowych
Mapy bitowej jest tablicą bitów, które określają kolor każdego piksela prostokątny tablicy pikseli. Liczba bitów przeznaczone danego piksela określa liczbę kolorów, które mogą być przypisane do tego pikseli. Na przykład, jeśli każdego piksela jest reprezentowany przez 4 bity, następnie piksela podanego można przypisać jedną 16 różnych kolorach (2 ^ 4 = 16). W poniższej tabeli przedstawiono kilka przykładów liczbę kolorów, które mogą zostać przypisani do piksela, reprezentowane przez daną liczbę bitów.  
  
|Liczba bitów na piksel|Liczbę kolorów, które mogą być przypisane do piksel|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Pliki dysku, które zazwyczaj przechowują mapy bitowe zawierają bloków informacyjnych, które przechowują informacje, takie jak liczba bitów na piksel, liczbę pikseli w każdym wierszu i liczbę wierszy w tablicy. Taki plik może również zawierać tabeli kolorów (czasami nazywany palety kolorów). Tabeli kolorów mapuje liczb w mapie bitowej konkretnych kolorów. Poniższa ilustracja przedstawia powiększony obraz wraz z jego tabeli mapy bitowej i kolor. Każdego piksela jest reprezentowany przez wartość 4-bitowej liczby, więc istnieją 2 ^ 4 = 16 kolorów w tabeli kolorów. Każdy kolor w tabeli jest reprezentowany przez liczbę 24-bitowego: 8 bitów czerwony, 8 bitów, zielonego i 8 bitów na niebieski. Liczby są wyświetlane w postaci szesnastkowej (podstawa 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Próbki mapy bitowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Spójrz na piksel w wierszu 3, w kolumnie 5 obrazu. Odpowiadającym im numerem w mapie bitowej to 1. Tabela kolorów informuje NAS 1 reprezentuje kolor czerwony, dzięki czemu piksel ma kolor czerwony. Wszystkie wpisy w górnym wierszu mapy bitowej to 3. Tabela kolorów informuje NAS 3 reprezentuje niebieski, więc wszystkie piksele w górnym wierszu obrazu są niebieski.  
  
> [!NOTE]
>  Niektóre mapy bitowe są przechowywane w formacie od dołu do góry. liczby w pierwszym wierszu mapy bitowej odpowiadają pikseli w dolnym wierszu obrazu.  
  
 Mapa bitowa, która przechowuje indeksy do tabeli kolorów nosi nazwę mapy bitowej indeksowane palety. Niektóre mapy bitowe nie ma potrzeby dla tabeli kolorów. Na przykład jeśli mapa bitowa używa 24 bity na piksel, tej mapy bitowej można przechowywać same kolory, a nie indeksy do tabeli kolorów. Poniższa ilustracja przedstawia mapy bitowej, która przechowuje bezpośrednio kolorów (24 bity na piksel) zamiast przy użyciu tabeli kolorów. Na ilustracji pokazano również powiększania widoku odpowiadających im obrazów. W mapie bitowej FFFFFF reprezentuje biały, FF0000 reprezentuje czerwony, 00FF00 reprezentuje kolor zielony i 0000FF reprezentuje niebieski.  
  
 ![Próbki mapy bitowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formaty plików graficznych  
 Istnieje wiele standardowych formatów Zapisywanie map bitowych w plikach na dysku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsługuje grafiki plików opisane w sekcjach.  
  
### <a name="bmp"></a>BMP  
 BMP to standardowy format używany przez Windows do przechowywania obrazów niezależnych od urządzenia i niezależny od aplikacji. Liczba bitów na piksel (1, 4, 8, 15, 24, 32 lub 64) dla danego pliku BMP jest określony w nagłówku pliku. Pliki BMP z 24 bity na piksel są powszechne. Pliki BMP nie zwykle są kompresowane i dlatego nie są dobrze nadaje się do przeniesienia w Internecie.  
  
### <a name="graphics-interchange-format-gif"></a>Graphics Interchange Format (GIF)  
 Obraz GIF jest to typowy format dla obrazów, które są wyświetlane na stronach sieci Web. Pliki GIF działa dobrze sprawdza się w rysunkach, obrazy, przy użyciu bloków jednolitego koloru i obrazów przy użyciu sharp granic między kolorów. Pliki GIF są kompresowane, ale żadne informacje nie są tracone w procesie kompresji; Po zdekompresowaniu obrazu jest dokładnie taka sama, co oryginalny. Jednego koloru w formacie GIF może być wyznaczony jako przezroczysty, tak, aby obraz, który będzie miał kolor tła, dowolnej strony sieci Web, który wyświetla go. Sekwencja obrazów GIF mogą być przechowywane w jednym pliku w celu utworzenia animowany plik GIF. Pliki GIF przechowywać maksymalnie 8 bitów na piksel, dzięki czemu są one ograniczone do 256 kolorów.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>JPEG (JPEG)  
 JPEG jest schemat kompresji, który sprawdza się w przypadku fizycznych sceny zeskanowane zdjęcia. Niektóre informacje są tracone w procesie kompresji, ale często jest imperceptible dla ludzkiego oka utraty. Pliki JPEG przechowywać 24 bity na piksel, dzięki czemu są one umożliwiająca wyświetlanie więcej niż 16 milionów kolorów. Pliki JPEG, które nie obsługują przezroczystość lub animacji.  
  
 Poziom kompresji obrazy JPEG jest konfigurowalne, ale wyższy poziom kompresji (mniejsze pliki) powoduje utratę więcej informacji. 20:1 kompresji często tworzy obraz odnajdującego ludzkiego oka trudne do odróżnienia od oryginału. Na poniższej ilustracji przedstawiono obraz BMP i dwa obrazy JPEG, które zostały skompresowane z tego obrazu BMP. Pierwszy JPEG ma stopień kompresji 4:1, a drugi JPEG ma kompresji o 8:1.  
  
 ![Przykłady typów plików](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Dekompresji JPEG nie działają dobrze w przypadku rysunki, bloki jednolitego koloru i ostrych granic. Poniższa ilustracja przedstawia BMP wraz z dwóch JPEG lub GIF. Pliki JPEG lub GIF zostały skompresowane z BMP. Stopień kompresji jest 4:1 dla GIF, 4:1 dla mniejszych JPEG, a następnie 8:3 dla większych JPEG. Pamiętaj, że plik GIF przechowuje sharp granice wzdłuż linii, ale JPEG mają tendencję do rozmycia granice.  
  
 ![Typy plików](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG jest schematu kompresji, nie w formacie pliku. Format wymiany plik JPEG (JFIF) to format pliku często używane do przechowywania i przesyłania obrazów, które zostały skompresowane zgodnie ze schematem JPEG. Pliki JFIF, wyświetlane przez przeglądarki sieci Web należy użyć rozszerzenia jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Plik Exchangeable Image (EXIF)  
 EXIF to format pliku używany do fotografii przechwycone przez aparaty cyfrowe. Plik EXIF zawiera obraz, który jest skompresowany zgodnie ze specyfikacją JPEG. Plik EXIF zawiera także informacje o zdjęcie (Data wykonania, migawki, szybkość, czas narażenia i tak dalej) i informacje na temat aparatu (producent, model i tak dalej).  
  
### <a name="portable-network-graphics-png"></a>Portable Network Graphics (PNG)  
 PNG format zachowuje wiele korzyści, w formacie GIF, ale również zapewnia możliwości poza tymi GIF. Podobnie jak pliki GIF PNG, pliki są kompresowane bez utraty informacji. Kolory z 8, 24 lub 48 bitów na piksel i liczby odcieni szarości z 1, 2, 4, 8 lub 16 bitów na piksel mogą być przechowywane pliki PNG. Z kolei plików GIF można użyć tylko 1, 2, 4 lub 8 bitów na piksel. Plik PNG można również przechowywać wartości alfa dla każdego piksela, który określa stopień, w którym kolor piksela jest zmieszana kolorem tła.  
  
 PNG usprawnieniem GIF możliwość stopniowo wyświetlania obrazu (oznacza to, aby wyświetlić skuteczniejszych przybliżeń obrazu, ponieważ nadejściu za pośrednictwem połączenia sieciowego). Pliki PNG może zawierać informacje korekcji gamma korekcji i kolor, tak, aby obrazy, które mogą być dokładnie renderowane na różnych urządzeniach wyświetlających.  
  
### <a name="tag-image-file-format-tiff"></a>Tag Image File Format (TIFF)  
 TIFF jest elastyczna i rozszerzalna formatu, który jest obsługiwany przez szerokiej gamy platform i aplikacji przetwarzania obrazów. TIFF, pliki można przechowywać obrazy z dowolnej liczby bitów na piksel i mogą stosować różne algorytmy kompresji. Kilka obrazów mogą być przechowywane w pliku TIFF pojedynczy, wielu stron. Informacje dotyczące obrazu (skanera upewnij, komputerze-hoście, typ kompresji, orientacji, próbki na pikseli i tak dalej), można przechowywane w pliku i uporządkowane przy użyciu tagów. Może być rozszerzona formacie TIFF, zgodnie z potrzebami, zatwierdzenia i dodawania nowych znaczników.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
