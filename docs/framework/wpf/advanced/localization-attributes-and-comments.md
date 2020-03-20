---
title: Lokalizacja atrybutów i komentarzy
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7281ca6d76f0d2ffb5020feba236b4e4cf948bdd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141591"
---
# <a name="localization-attributes-and-comments"></a>Lokalizacja atrybutów i komentarzy
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]komentarze lokalizacji są właściwości, wewnątrz kodu źródłowego XAML, dostarczone przez deweloperów, aby zapewnić reguły i wskazówki dotyczące lokalizacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Komentarze dotyczące lokalizacji zawierają dwa zestawy informacji: atrybuty lokalizacji i komentarze do lokalizacji swobodnej. Atrybuty lokalizacji są używane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przez interfejs API lokalizacji, aby wskazać, które zasoby mają być zlokalizowane. Komentarze w postaci wolnych od czynów to informacja, którą autor aplikacji chce dołączyć.  

<a name="Localizer_Comments_"></a>
## <a name="localization-comments"></a>Komentarze do lokalizacji  
 Jeśli autorzy aplikacji znaczników mają wymagania dotyczące określonych elementów w języku XAML, takie jak ograniczenia dotyczące długości tekstu, rodziny czcionek lub rozmiaru czcionki, mogą przekazać te informacje lokalizatorom z komentarzami w kodzie XAML. Proces dodawania komentarzy do kodu źródłowego jest następujący:  
  
1. Deweloper aplikacji dodaje komentarze lokalizacji do kodu źródłowego XAML.  
  
2. Podczas procesu kompilacji można określić w pliku proj, czy pozostawić komentarze lokalizacji swobodnej w zestawie, usunąć część komentarzy lub usunąć wszystkie komentarze. Okrojone komentarze są umieszczane w oddzielnym pliku. Możesz określić opcję `LocalizationDirectivesToLocFile` za pomocą tagu, np.:  
  
     `<LocalizationDirectivesToLocFile>`*wartość*`</LocalizationDirectivesToLocFile>`  
  
3. Wartości, które można przypisać to:  
  
    - **Brak** — zarówno komentarze, jak i atrybuty pozostają wewnątrz zestawu i nie jest generowany żaden oddzielny plik.  
  
    - **CommentsOnly** - Paski tylko komentarze z zestawu i umieszcza je w oddzielnym LocFile.  
  
    - **Wszystkie** — paski zarówno komentarze, jak i atrybuty z zestawu i umieszcza je zarówno w oddzielnym LocFile.  
  
4. Gdy zasoby zlokalizowane są wyodrębniane z BAML, atrybuty lokalizacji są przestrzegane przez interfejs API lokalizacji BAML.  
  
5. Pliki komentarzy lokalizacji, zawierające tylko komentarze w postaci swobodnej, są włączane do procesu lokalizacji w późniejszym czasie.  
  
 W poniższym przykładzie pokazano, jak dodać komentarze lokalizacji do pliku XAML.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 W poprzednim przykładzie Localization.Attributes sekcja zawiera atrybuty lokalizacji i Localization.Comments sekcji komentarze w postaci swobodnej. W poniższych tabelach przedstawiono atrybuty i komentarze oraz ich znaczenie dla lokalizatora.  
  
|Atrybuty lokalizacji|Znaczenie|  
|-----------------------------|-------------|  
|$Content (niemodyfikowalny tekst czytelny)|Nie można zmodyfikować zawartości elementu TextBlock. Lokalizatory nie można zmienić wyrazu "Microsoft". Zawartość jest widoczna (czytelna) dla lokalizatora. Kategorią zawartości jest tekst.|  
|FontFamily (niemodyfikowalna czytelność)|Nie można zmienić właściwości rodziny czcionek elementu TextBlock, ale jest on widoczny dla localizera.|  
  
|Komentarze o wolnych formularzach lokalizacji|Znaczenie|  
|--------------------------------------|-------------|  
|$Content (znak towarowy)|Autor aplikacji informuje localizer, że zawartość w TextBlock element jest znakiem towarowym.|  
|FontSize (rozmiar czcionki znaku towarowego)|Autor aplikacji wskazuje, że właściwość rozmiar czcionki powinna być zgodna ze standardowym rozmiarem znaku towarowego.|  
  
### <a name="localizability-attributes"></a>Atrybuty lokalizacji  
 Informacje w Localization.Attributes zawiera listę par: nazwa wartości docelowej i skojarzone wartości lokalizacji. Nazwa obiektu docelowego może być nazwą właściwości lub nazwą $Content specjalnego. Jeśli jest to nazwa właściwości, wartość docelowa jest wartością właściwości. Jeśli jest $Content, wartość docelowa jest zawartość elementu.  
  
 Istnieją trzy typy atrybutów:  
  
- **Kategoria**. Określa, czy wartość powinna być modyfikowana za pomocą narzędzia lokalizatora. Zobacz: <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Czytelność**. Określa, czy narzędzie lokalizatora powinien odczytywać (i wyświetlać) wartość. Zobacz: <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Możliwość modyfikacji**. Określa, czy narzędzie lokalizatora umożliwia modyfikację wartości. Zobacz: <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Te atrybuty można określić w dowolnej kolejności rozdzielone przez spację. W przypadku, gdy zostaną określone zduplikowane atrybuty, ostatni atrybut zastąpi poprzednie. Na przykład Localization.Attributes = "Unmodifiable Modifiable" ustawia możliwość modyfikacji do modyfikowalności, ponieważ jest to ostatnia wartość.  
  
 Modyfikowalność i czytelność są oczywiste. Atrybut Kategoria zawiera wstępnie zdefiniowane kategorie, które pomagają lokalizatorowi podczas tłumaczenia tekstu. Kategorie, takie jak Tekst, Etykieta i Tytuł, dają lokalizatorowi informacje o tym, jak przetłumaczyć tekst. Istnieją również kategorie specjalne: Brak, Dziedzicz, Ignoruj i NeverLocalize.  
  
 W poniższej tabeli przedstawiono znaczenie kategorii specjalnych.  
  
|Kategoria|Znaczenie|  
|--------------|-------------|  
|Brak|Wartość docelowa nie ma zdefiniowanej kategorii.|  
|Dziedziczą|Wartość docelowa dziedziczy swoją kategorię z nadrzędnego.|  
|Zignoruj|Wartość docelowa jest ignorowana w procesie lokalizacji. Ignoruj wpływa tylko na bieżącą wartość. Nie wpłynie to na węzły podrzędne.|  
|NeverLocalize (Niemkłda)|Bieżąca wartość nie może być zlokalizowana. Ta kategoria jest dziedziczona przez elementy podrzędne elementu.|  
  
<a name="Localization_Comments"></a>
## <a name="localization-comments"></a>Komentarze do lokalizacji  
 Localization.Comments zawiera ciągi swobodne dotyczące wartości docelowej. Deweloperzy aplikacji można dodać informacje, aby dać localizers wskazówki dotyczące sposobu tłumaczenia tekstu aplikacji. Format komentarzy może być dowolny ciąg otoczony "()". Użyj\\' ' , aby uciec znaków.  
  
## <a name="see-also"></a>Zobacz też

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Używanie automatycznego układu do utworzenia przycisku](how-to-use-automatic-layout-to-create-a-button.md)
- [Używanie siatki do automatycznego układu](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
