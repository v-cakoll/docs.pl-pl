---
title: Lokalizacja atrybutów i komentarzy
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: a9d01b7cebea845ad67d846af5b08f59977b8cd6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301857"
---
# <a name="localization-attributes-and-comments"></a>Lokalizacja atrybutów i komentarzy
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Lokalizacja komentarzy są właściwościami, wewnątrz [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kod źródłowy, dostarczone przez deweloperów, które zapewniają reguły i wskazówki dla lokalizacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Lokalizacja komentarzy zawierają dwa zestawy danych: atrybuty przeglądu możliwości lokalizacji i komentarze w dowolnej lokalizacji. Możliwości zlokalizowania atrybuty są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacji interfejsu API, aby wskazać, które zasoby mają być lokalizowany. Wszystkie informacje, które aplikacja chce, aby uwzględnić znajdują się w dowolnej postaci komentarze.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Lokalizacja komentarzy  
 Jeśli autorzy aplikacji znaczników mają wymagania dotyczące określonych elementów w [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], takie jak ograniczenia dotyczące długość tekstu rodzinę czcionek i rozmiar czcionki, ich przekazywanie tych informacji do lokalizatorzy z komentarzami w [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kodu. Proces dodawania komentarzy do kodu źródłowego jest w następujący sposób:  
  
1. Deweloper aplikacji dodaje komentarze lokalizacji, aby [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kodu źródłowego.  
  
2. Podczas procesu kompilacji można określić w pliku .proj czy zamieszczać komentarze dowolnej lokalizacji w zestawie, pasek się częścią komentarze lub pasek się wszystkie komentarze. Komentarze usunięta, a limit są umieszczane w oddzielnym pliku. Określ, przy użyciu opcji `LocalizationDirectivesToLocFile` tagu, na przykład:  
  
     `<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`  
  
3. Wartości, które mogą być przypisane są następujące:  
  
    -   **Brak** — zarówno komentarzy i atrybutów pozostają w zestawie i generowany jest ten sam plik.  
  
    -   **CommentsOnly** — usuwa tylko komentarze z zestawu i umieszcza je w oddzielnym LocFile.  
  
    -   **Wszystkie** — usuwa komentarzy i atrybutów z zestawu i umieszczane zarówno w oddzielnych LocFile.  
  
4. Gdy lokalizowalne zasoby są wyodrębniane z [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], atrybuty możliwości zlokalizowania są przestrzegane przez [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] lokalizacji interfejsu API.  
  
5. Pliki komentarzy lokalizacji, zawierający tylko dowolne komentarze są włączone do proces lokalizacji w późniejszym czasie.  
  
 Poniższy przykład pokazuje, jak dodawać komentarze lokalizacji [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 W poprzednim przykładzie Localization.Attributes sekcja zawiera atrybuty lokalizacji i komentarze sekcji swobodne Localization.Comments. W poniższej tabeli przedstawiono atrybuty i komentarze oraz ich znaczenie do lokalizatorowi.  
  
|Lokalizacja atrybutów|Znaczenie|  
|-----------------------------|-------------|  
|$Content (niemodyfikowalnych tekst do odczytu)|Nie można zmodyfikować zawartość elementu TextBlock. Lokalizatorzy nie można zmienić słowo "Microsoft". Zawartość jest widoczna (elementu Readable) lokalizatorowi. Kategoria zawartości jest tekst.|  
|FontFamily (Niemodyfikowalnych do odczytu)|Nie można zmienić właściwości rodziny czcionek elementu TextBlock, ale jest widoczny dla lokalizatorowi.|  
  
|Lokalizacja dowolne komentarze|Znaczenie|  
|--------------------------------------|-------------|  
|$Content (znak towarowy)|Autor aplikacji lokalizatorowi informuje, czy zawartość w elemencie TextBlock jest znakiem towarowym firmy.|  
|FontSize (rozmiar czcionki znaku towarowego)|Autor aplikacji oznacza, że właściwość rozmiar czcionki, należy wykonać rozmiar znaków towarowych.|  
  
### <a name="localizability-attributes"></a>Atrybuty przeglądu możliwości lokalizacji  
 Informacje przedstawione w Localization.Attributes zawiera listę par: wartości skojarzone przeglądu możliwości lokalizacji i nazwę wartości docelowej. Nazwa docelowego może być nazwa właściwości lub nazwę $Content specjalne. Jeśli nazwa właściwości, wartość docelowa jest wartość właściwości. Jeśli jest to $Content, wartość docelowa jest zawartość elementu.  
  
 Istnieją trzy typy atrybutów:  
  
-   **Kategoria**. Określa, czy wartość powinna być można modyfikować za pomocą narzędzia lokalizatorowi. Zobacz <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Czytelność**. Określa, czy narzędzie lokalizatorowi należy odczytać (i wyświetlić) wartość. Zobacz <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability**. Określa, czy narzędzie lokalizatorowi zezwala na wartość ma zostać zmodyfikowana. Zobacz <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Te atrybuty można określić w dowolnej kolejności, rozdzielonych spacją. W przypadku, gdy określono zduplikowane atrybuty, wartość ostatniego atrybutu zostaną przesłonięte poprzedniej wersji portalu. Na przykład Localization.Attributes = "Niemodyfikowalnych modyfikowalnymi" Ustawia Modifiability do Modifiable, ponieważ jest ostatnią wartość.  
  
 Modifiability i czytelności, nie wymaga wyjaśnień. Atrybut Kategoria zawiera wstępnie zdefiniowane kategorie, które pomagają lokalizatorowi podczas tłumaczenia tekstu. Kategorie, takie jak tekst, etykiety i tytuł zapewniają lokalizatorowi informacje o sposobie tłumaczenie tekstu. Istnieją również specjalne kategorie: Brak, dziedziczenie, zignoruj i NeverLocalize.  
  
 W poniższej tabeli przedstawiono znaczenie specjalnych kategoriach.  
  
|Kategoria|Znaczenie|  
|--------------|-------------|  
|Brak|Wartość docelowa jest nie zdefiniowanych kategorii.|  
|Dziedziczenie|Wartość docelowa dziedziczy jego kategoria od jego elementu nadrzędnego.|  
|Zignoruj|Wartość docelowa jest ignorowany w procesie lokalizacji. Ignoruj dotyczy tylko bieżącej wartości. Nie wpłynie węzłów podrzędnych.|  
|NeverLocalize|Bieżąca wartość nie może być zlokalizowany. Ta kategoria jest dziedziczona przez elementy podrzędne elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Lokalizacja komentarzy  
 Localization.Comments zawiera ciągów dotyczące wartości docelowej. Deweloperzy aplikacji mogą dodawać informacje, aby zapewnić lokalizatorzy wskazówek na temat sposób przekształcania tekstu aplikacji. Format komentarze może być dowolnym ciągiem, ujęte w "()". Użyj "\\" jako znak ucieczki dla znaków.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Używanie automatycznego układu do utworzenia przycisku](how-to-use-automatic-layout-to-create-a-button.md)
- [Używanie siatki do automatycznego układu](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
