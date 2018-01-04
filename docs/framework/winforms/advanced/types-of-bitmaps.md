---
title: Typy map bitowych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6af28e7b50cb7e4a2a90153a053a83931c738214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-bitmaps"></a>Typy map bitowych
Mapy bitowej jest tablicą bitów, które określają koloru każdego piksela w tablicy regularnej pikseli. Liczba bitów przeznaczonych do danego piksela określa liczbę kolorów, które można przypisać do piksela. Na przykład jeśli każdego piksela jest reprezentowana przez 4 bity, następnie danego pikseli można przypisać jedną 16 kolorów różnych (2 ^ 4 = 16). W poniższej tabeli przedstawiono kilka przykładów liczbę kolorów, które można przypisać do piksela reprezentowany przez daną liczbę bitów.  
  
|Bity na piksel|Liczba kolorów, które można przypisać do piksel|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Pliki dysku, które przechowują map bitowych zwykle zawierają bloków informacyjnych, które przechowują informacje, takie jak liczba bitów na piksel, liczbę pikseli w każdym wierszu i liczbę wierszy w tablicy. Taki plik może również zawierać tabeli kolorów (nazywane również paletę kolorów). Tabeli kolorów mapy numery w mapie bitowej do określonych kolorów. Na poniższej ilustracji przedstawiono powiększony obraz wraz ze swoją tabelą mapy bitowej i kolor. Każdego piksela jest reprezentowany przez wartość 4-bitowej liczby co 2 ^ 4 = 16 kolorów w tabeli kolorów. Każdy kolorów w tabeli jest reprezentowana przez 24-bitową liczbą: 8 bitów czerwony, 8 bitów zielonego i 8 bitów dla niebieski. Numery są wyświetlane w postaci szesnastkowej (podstawa 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Próbki mapy bitowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Spójrz na piksel w wierszu 3, w kolumnie 5 obrazu. Odpowiedni numer w mapy bitowej jest 1. W tabeli kolorów informuje NAS 1 reprezentuje kolor czerwony, więc piksela jest czerwony. Wszystkie wpisy w górnym wierszu mapy bitowej to 3. W tabeli kolorów informuje NAS 3 reprezentuje blue, więc wszystkie piksele w górnym wierszu obrazu niebieski.  
  
> [!NOTE]
>  Niektóre mapy bitowe są przechowywane w formacie dołu do góry. numery w pierwszym wierszu mapy bitowej odpowiadają pikseli w ostatnim wierszu obrazu.  
  
 Przechowujący indeksów w tabeli kolorów mapy bitowej jest nazywany mapy bitowej indeksowane palety. Niektóre mapy bitowe nie ma potrzeby dla tabeli kolorów. Na przykład jeśli mapy bitowej używa 24 bitów na piksel, aktualnego można przechowywać same kolory zamiast indeksów w tabeli kolorów. Na poniższej ilustracji przedstawiono mapę bitową przechowujący kolorów bezpośrednio (24 bitów na piksel) zamiast przy użyciu tabeli kolorów. Na ilustracji przedstawiono również powiększania widoku odpowiedniego obrazu. W pliku mapy bitowej FFFFFF reprezentuje białe, FF0000 reprezentuje czerwony 00FF00 reprezentuje kolor zielony i 0000FF reprezentuje niebieski.  
  
 ![Próbki mapy bitowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formaty plików graficznych  
 Istnieje wiele standardowych formatów Zapisywanie map bitowych w plikach na dysku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]obsługuje grafiki plików opisane w sekcjach.  
  
### <a name="bmp"></a>BMP  
 BMP jest to standardowy format używany przez system Windows do przechowywania obrazów niezależne od urządzenia i aplikacji. Liczba bitów na piksel (1, 4, 8, 15, 24, 32 lub 64) dla danego pliku BMP jest określona w nagłówku pliku. Pliki BMP z 24 bitów na piksel są często używane. Pliki BMP nie zwykle są kompresowane i, w związku z tym nie są dobrze nadają się do przeniesienia w Internecie.  
  
### <a name="graphics-interchange-format-gif"></a>Graphics Interchange Format (GIF)  
 GIF jest wspólnego formatu obrazów, które są wyświetlane na stronach sieci Web. Plików GIF działa dobrze w przypadku rysunki, obrazy z bloków pełnego koloru i obrazy z sharp granicę między kolorów. Pliki GIF są kompresowane, ale żadne informacje nie są tracone w procesie kompresji; zdekompresowanych obrazu jest dokładnie taka sama jak oryginalne. Jeden z plików GIF kolorów może zostać wyznaczony jako przezroczysty, dzięki czemu obraz będzie mieć kolor tła dowolnej strony sieci Web, który wyświetla go. Sekwencja GIF obrazy mogą być przechowywane w jednym pliku do utworzenia animowany plik GIF. Pliki GIF przechowywać maksymalnie 8 bitów na piksel, dzięki czemu są one ograniczone do 256 kolorów.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>JPEG (JPEG)  
 JPEG jest schemat kompresji, który dobrze fizycznych sceny, takich jak skanowane fotografie. Niektóre informacje są tracone w procesie kompresji, ale często jest imperceptible dla człowieka oka utraty. JPEG przechowywać 24 bitów na piksel, dzięki czemu są one umożliwiająca wyświetlanie więcej niż 16 milionów kolorów. JPEG nie obsługują przezroczystość lub animacji.  
  
 Konfiguruje się poziom kompresji obrazy JPEG, ale wyższe poziomy kompresji (mniejsze pliki) powodują utratę więcej informacji. 20:1 kompresji często tworzy obraz wyszukującą ludzkiego oka trudne do odróżnienia od oryginału. Na poniższej ilustracji przedstawiono obrazu w formacie BMP i dwa obrazy JPEG skompresowane z tego obrazu BMP. Pierwszy JPEG ma kompresji 4:1, a drugi JPEG ma kompresji o 8:1.  
  
 ![Przykłady typów plików](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Dekompresji JPEG nie działa także dla rysunki, bloki pełny kolor i ostrych granic. Na poniższej ilustracji przedstawiono BMP wraz z dwóch JPEG i GIF. JPEG i plik GIF były kompresowane z BMP. Stopień kompresji jest 4:1 w przypadku GIF, 4:1 dla mniejszych JPEG i 8:3 dla większych JPEG. Pamiętaj, że plik GIF zachowuje sharp granice wzdłuż linii, ale JPEG mają tendencję do rozmycia granice.  
  
 ![Typy plików](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG jest schemat kompresji nie format pliku. Format wymiany plik JPEG (JFIF) to powszechnie używany do przechowywania i przesyłania obrazów skompresowane zgodnie ze schematem JPEG format pliku. Pliki JFIF wyświetlane przez przeglądarki sieci Web należy użyć rozszerzenia jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Plik obrazu wymienne (EXIF)  
 EXIF to format pliku używany do fotografii przechwycone przez aparaty cyfrowe. Plik EXIF zawiera obraz, który jest skompresowany według specyfikacji JPEG. Plik EXIF zawiera także informacje o zdjęcie (Data wykonania, migawki szybkość, czas ekspozycji i tak dalej) i informacje na temat aparatu (producenta, model i tak dalej).  
  
### <a name="portable-network-graphics-png"></a>Portable Network Graphics (PNG)  
 PNG format zachowuje wiele zalet formacie GIF, ale również zapewnia możliwości poza tymi GIF. Podobnie jak pliki GIF PNG, pliki są kompresowane bez utraty informacji. PNG, pliki można przechowywać i 8, 24 lub 48 bitów na piksel i liczby odcieni szarości z 1, 2, 4, 8 lub 16 bitów na piksel kolorów. Z kolei pliki GIF, można użyć tylko 1, 2, 4 lub 8 bitów na piksel. Plik PNG można również przechowywać wartość alfa dla każdego piksela, który określa stopień, do którego kolor piksela jest mieszane kolorem tła.  
  
 Możliwości stopniowo wyświetlania obrazu PNG usprawnia GIF (oznacza to, aby wyświetlić skuteczniejszych przybliżenia obrazu, ponieważ dociera przy użyciu połączenia sieciowego). PNG, pliki może zawierać informacje korekcji gamma korekty i kolor tak, aby obrazy mogą być dokładnie renderowane w różnych wyświetlania na urządzeniach.  
  
### <a name="tag-image-file-format-tiff"></a>Tag Image File Format (TIFF)  
 TIFF jest elastyczny i rozszerzalna formatu, który jest obsługiwany przez różnych platform i aplikacji przetwarzania obrazów. TIFF, pliki przechowywania obrazów z dowolnej liczby bitów na piksel i można stosować różne algorytmy kompresji. Kilka obrazów mogą być przechowywane w jednej, wielu stron plik TIFF. Informacje dotyczące obrazu (skanera upewnij, komputer-host, typ kompresji, orientacji, próbek na piksel i tak dalej) można przechowywane w pliku i ułożone przy użyciu tagów. TIFF format można rozszerzyć, odpowiednio do potrzeb zatwierdzenia i dodawania nowych znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Image?displayProperty=nameWithType>  
 <xref:System.Drawing.Bitmap?displayProperty=nameWithType>  
 <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
