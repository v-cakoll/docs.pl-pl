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
ms.openlocfilehash: 2243c9ce2d8ba741143d301c38e8b88d7b196c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914827"
---
# <a name="types-of-bitmaps"></a>Typy map bitowych
Mapa bitowa jest tablicą bitów, która określa kolor każdego piksela w prostokątnym tablicy pikseli. Liczba bitów przeznaczonych dla poszczególnych pikseli określa liczbę kolorów, które można przypisać do tego piksela. Na przykład, jeśli każdy piksel jest reprezentowany przez 4 bity, wówczas dany piksel można przypisać jeden z 16 różnych kolorów (2 ^ 4 = 16). W poniższej tabeli przedstawiono kilka przykładów liczby kolorów, które można przypisać do piksela reprezentowanego przez daną liczbę bitów.  
  
|Bity na piksel|Liczba kolorów, które można przypisać do piksela|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Pliki dysku, które przechowują mapy bitowe, zwykle zawierają jeden lub więcej bloków informacji, które przechowują informacje, takie jak liczba bitów na piksel, liczba pikseli w każdym wierszu i liczba wierszy w tablicy. Taki plik może również zawierać tabelę kolorów (czasami nazywaną paletą kolorów). Tabela kolorów mapuje liczby w mapie bitowej na określone kolory. Na poniższej ilustracji przedstawiono powiększony obraz wraz z jego mapą bitową i tabelą kolorów. Każdy piksel jest reprezentowany przez 4-bitową liczbę, więc w tabeli kolorów istnieją 2 ^ 4 = 16 kolorów. Każdy kolor w tabeli jest reprezentowany przez 24-bitową liczbę: 8 bitów na czerwony, 8 bitów dla zielono i 8 bitów dla niebieskiego. Liczby są wyświetlane w formacie szesnastkowym (Base 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Mapa bitowa — przykład](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Spójrz na piksel w wierszu 3, kolumnie 5 obrazu. Odpowiadająca im liczba w mapie bitowej to 1. Tabela kolorów informuje nas, że wartość 1 oznacza kolor czerwony, więc piksel jest czerwony. Wszystkie wpisy w górnym wierszu mapy bitowej to 3. Tabela kolorów informuje nas, że 3 reprezentuje niebieską, więc wszystkie piksele w górnym wierszu obrazu są niebieskie.  
  
> [!NOTE]
> Niektóre mapy bitowe są przechowywane w formacie do dołu. liczby w pierwszym wierszu mapy bitowej odnoszą się do pikseli w dolnym wierszu obrazu.  
  
 Mapa bitowa przechowująca indeksy w tabeli kolorów jest nazywana mapą bitową indeksowaną z paletą. Niektóre mapy bitowe nie wymagają żadnej tabeli koloru. Na przykład, jeśli mapa bitowa używa 24 bitów na piksel, mapa bitowa może przechowywać same kolory zamiast indeksów w tabeli kolorów. Na poniższej ilustracji przedstawiono mapę bitową, która przechowuje kolory bezpośrednio (24 bity na piksel) zamiast korzystać z tabeli kolorów. Ilustracja pokazuje również powiększony widok odpowiedniego obrazu. W mapie bitowej FFFFFF reprezentuje biały, FF0000 reprezentuje czerwony, 00FF00 reprezentuje zieloną, a 0000FF reprezentuje niebieską.  
  
 ![Mapa bitowa — przykład](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formaty plików graficznych  
 Istnieje wiele standardowych formatów zapisywania map bitowych w plikach dyskowych. Interfejs GDI+ obsługuje formaty plików graficznych opisane w poniższych akapitach.  
  
### <a name="bmp"></a>BMP  
 BMP to standardowy format używany przez system Windows do przechowywania obrazów niezależnych od urządzenia i niezależnych od aplikacji. Liczba bitów na piksel (1, 4, 8, 15, 24, 32 lub 64) dla danego pliku BMP jest określona w nagłówku pliku. Pliki BMP zawierające 24 bity na piksel są wspólne. Pliki BMP nie są zwykle skompresowane i dlatego nie są dobrze dopasowane do transferu przez Internet.  
  
### <a name="graphics-interchange-format-gif"></a>Graphics Interchange Format (GIF)  
 GIF jest popularnym formatem dla obrazów, które są wyświetlane na stronach sieci Web. Pliki GIF działają dobrze dla rysunków liniowych, obrazów z blokami pełnego koloru i obrazów z ostrymi granicami między kolorami. Pliki GIF są skompresowane, ale w procesie kompresji nie są tracone żadne informacje. skompresowany obraz jest dokładnie taki sam, jak oryginalny. Jeden kolor w formacie GIF można wyznaczyć jako przezroczysty, dzięki czemu obraz będzie miał kolor tła dowolnej strony sieci Web, która go wyświetla. Sekwencja obrazów GIF może być przechowywana w jednym pliku, aby utworzyć animowany plik GIF. Program GIF przechowuje maksymalnie 8 bitów na piksel, więc są one ograniczone do 256 kolorów.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG jest schematem kompresji, który dobrze sprawdza się w przypadku naturalnych scen, takich jak zeskanowane fotografie. Niektóre informacje są tracone w procesie kompresji, ale często utrata jest niezauważalna dla człowieka. JPEG przechowuje 24 bity na piksel, dzięki czemu mogą wyświetlać więcej niż 16 000 000 kolorów. Pliki JPEG nie obsługują przezroczystości ani animacji.  
  
 Poziom kompresji w obrazach JPEG jest konfigurowalny, ale wyższe poziomy kompresji (mniejsze pliki) powodują zwiększenie utraty informacji. Współczynnik kompresji 20:1 często generuje obraz, który jest trudny do odróżnienia od oryginału przez człowieka. Na poniższej ilustracji przedstawiono obraz BMP i dwa obrazy JPEG, które zostały skompresowane z tego obrazu BMP. Pierwszy JPEG ma współczynnik kompresji 4:1, a drugi JPEG ma współczynnik kompresji około 8:1.  
  
 ![Przykłady dla typ_pliku](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Kompresja JPEG nie działa dobrze w przypadku rysunków liniowych, bloków pełnego koloru i ostrych granic. Na poniższej ilustracji przedstawiono BMP wraz z dwoma JPEG i GIF. Pliki JPEG i GIF zostały skompresowane z BMP. Współczynnik kompresji to 4:1 dla formatu GIF, 4:1 dla mniejszego JPEG i 8:3 dla większego JPEG. Należy pamiętać, że plik GIF utrzymuje ostre granice wzdłuż linii, ale pliki JPEG mają rozmycie granic.  
  
 ![Typ](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG jest schematem kompresji, a nie formatem pliku. JPEG File Interchange Format (JFIF) to format pliku często używany do przechowywania i przesyłania skompresowanych obrazów zgodnie ze schematem JPEG. Pliki JFIF wyświetlane przez przeglądarki sieci Web używają rozszerzenia jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Plik obrazu z wymianą (EXIF)  
 EXIF to format pliku używany w przypadku fotografii przechwytywanych przez cyfrowe aparaty fotograficzne. Plik EXIF zawiera obraz skompresowany zgodnie ze specyfikacją JPEG. Plik EXIF zawiera również informacje o zdjęciu (Data wykonania, szybkość migawki, czas ekspozycji itp.) oraz informacje o aparacie (producenta, modelu itd.).  
  
### <a name="portable-network-graphics-png"></a>Portable Network Graphics (PNG)  
 Format PNG zachowuje wiele zalet formatu GIF, ale udostępnia również funkcje wykraczające poza formaty GIF. Podobnie jak pliki GIF, pliki PNG są kompresowane bez utraty informacji. Pliki PNG mogą przechowywać kolory z 8, 24 lub 48 bitów na piksel i Skala szarości z 1, 2, 4, 8 lub 16 bitów na piksel. Z kolei pliki GIF mogą korzystać tylko z 1, 2, 4 lub 8 bitów na piksel. Plik PNG może również przechowywać wartość alfa dla każdego piksela, która określa stopień mieszania koloru piksela z kolorem tła.  
  
 Format PNG jest ulepszony w formacie GIF w celu stopniowego wyświetlania obrazu (czyli do wyświetlania lepszych i lepszych przybliżeń obrazu w miarę docierania przez połączenie sieciowe). Pliki PNG mogą zawierać korekcję gamma i informacje o korekcji kolorów, dzięki czemu obrazy mogą być prawidłowo renderowane na różnych urządzeniach wyświetlających.  
  
### <a name="tag-image-file-format-tiff"></a>Tag Image File Format (TIFF)  
 TIFF to elastyczny i rozszerzalny format obsługiwany przez szeroką gamę platform i aplikacji do przetwarzania obrazów. Pliki TIFF mogą przechowywać obrazy z dowolną liczbą bitów na piksel i mogą wykorzystywać różne algorytmy kompresji. Kilka obrazów może być przechowywanych w jednym, wielostronicowym pliku TIFF. Informacje powiązane z obrazem (marka, komputer-host, typ kompresji, Orientacja, przykłady na piksel i tak dalej) mogą być przechowywane w pliku i uporządkowane przy użyciu tagów. Format TIFF można rozszerzyć odpowiednio do wymagań zatwierdzania i dodawania nowych tagów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
