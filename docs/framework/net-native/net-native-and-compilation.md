---
title: Architektura .NET Native i kompilacja
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
ms.openlocfilehash: cf5c9f05b2f2cb4ca15e4add5b53bc9bdca757a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128246"
---
# <a name="net-native-and-compilation"></a>Architektura .NET Native i kompilacja

Windows 8.1 aplikacji i aplikacji klasycznych systemu Windows, które są przeznaczone dla platformy the.NET Framework, są zapisywane w określonym języku programowania i kompilowane w języku pośrednim (IL). W czasie wykonywania kompilator "just-in-Time" (JIT) jest odpowiedzialny za kompilowanie kodu IL w kodzie macierzystym komputera lokalnego tuż przed wykonaniem metody po raz pierwszy. Z kolei łańcuch narzędzi .NET Native konwertuje kod źródłowy na kod natywny w czasie kompilacji. W tym temacie porównano .NET Native z innymi technologiami kompilacji dostępnymi dla .NET Framework aplikacji, a także praktyczne omówienie sposobu, w jaki .NET Native generuje kod natywny, który może pomóc zrozumieć, dlaczego Wyjątki występujące w kodzie skompilowanym z platformą .NET Natywne nie występują w kodzie skompilowanym przez JIT.

## <a name="net-native-generating-native-binaries"></a>.NET Native: generowanie natywnych plików binarnych

Aplikacja, która jest przeznaczona dla .NET Framework i która nie jest skompilowana za pomocą łańcucha narzędzi .NET Native, składa się z zestawu aplikacji, który obejmuje następujące elementy:

- [Metadane](../../standard/metadata-and-self-describing-components.md) opisujące zestaw, jego zależności, typy, które zawiera, oraz ich członków. Metadane są używane na potrzeby odbicia i dostępu z późnym wiązaniem, a także w niektórych przypadkach za pomocą kompilatora i narzędzi do tworzenia.

- Kod implementacji. Obejmuje to kod w języku pośrednim (IL). W czasie wykonywania kompilator just-in-Time (JIT) tłumaczy go na kod natywny dla platformy docelowej.

 Oprócz zestawu aplikacji głównej, aplikacja musi mieć następujące elementy:

- Wszystkie dodatkowe biblioteki klas lub zestawy innych firm, które są wymagane przez aplikację. Te zestawy są podobne do metadanych, które opisują zestaw, jego typy i ich składowe, a także IL, który implementuje wszystkie elementy członkowskie typu.

- Biblioteka klas .NET Framework. Jest to kolekcja zestawów zainstalowanych w systemie lokalnym z instalacją .NET Framework. Zestawy zawarte w bibliotece klas .NET Framework obejmują pełny zestaw metadanych i kod implementacji.

- Środowisko uruchomieniowe języka wspólnego. Jest to zbiór bibliotek dołączanych dynamicznie, które wykonują takie usługi, jak ładowanie zestawów, zarządzanie pamięcią i wyrzucanie elementów bezużytecznych, obsługa wyjątków, kompilacja just in Time, komunikacja zdalna i międzyoperacyjność. Podobnie jak w przypadku biblioteki klas środowisko uruchomieniowe jest instalowane w systemie lokalnym w ramach instalacji .NET Framework.

Należy pamiętać, że cały środowisko uruchomieniowe języka wspólnego, a także metadane i IL dla wszystkich typów w zestawach specyficznych dla aplikacji, zestawy stron trzecich i zestawy systemowe muszą być obecne, aby można było pomyślnie wykonać aplikację.

## <a name="net-native-and-just-in-time-compilation"></a>Kompilacja .NET Native i just-in-Time

Dane wejściowe dla łańcucha narzędzi .NET Native to aplikacja ze sklepu Windows skompilowana przez kompilator C# lub Visual Basic. Innymi słowy, łańcuch narzędzi .NET Native rozpoczyna wykonywanie, gdy kompilator języka zakończył kompilację aplikacji ze sklepu Windows.

> [!TIP]
> Ponieważ dane wejściowe do .NET Native to IL i metadane zapisywane w zestawach zarządzanych, można nadal wykonywać niestandardowe generowanie kodu lub inne niestandardowe operacje przy użyciu zdarzeń przed kompilacją lub po kompilacji lub modyfikując plik projektu MSBuild.
>
> Jednak kategorie narzędzi modyfikujących IL, które uniemożliwiają analizowanie danych IL aplikacji przez łańcuch narzędzi programu .NET, nie są obsługiwane. Narzędzia dla innych typów są najbardziej znaczące.

W trakcie konwertowania aplikacji z IL na kod natywny łańcuch narzędzi .NET Native wykonuje operacje podobne do następujących:

- W przypadku niektórych ścieżek kodu zastępuje on kod, który opiera się na odbiciu i metadanych przy użyciu statycznego kodu natywnego. Na przykład, jeśli typ wartości nie przesłania metody <xref:System.ValueType.Equals%2A?displayProperty=nameWithType>, domyślny test dla równości używa odbicia, aby pobrać obiekty <xref:System.Reflection.FieldInfo> reprezentujące pola typu wartości, a następnie porównuje wartości pól dwóch wystąpień. Podczas kompilowania do kodu natywnego łańcuch narzędzi .NET Native zastępuje kod odbicia i metadane przy użyciu statycznego porównania wartości pól.

- Jeśli to możliwe, próbuje wyeliminować wszystkie metadane.

- Obejmuje ona tylko kod implementacji, który jest faktycznie wywoływany przez aplikację. W szczególności ma to wpływ na kod w bibliotekach innych firm i w bibliotece klas .NET Framework. W związku z tym aplikacja nie jest już zależała od bibliotek innych firm ani pełnej biblioteki klas .NET Framework. Zamiast tego kod w bibliotekach klas innych firm i .NET Framework jest teraz lokalny dla aplikacji.

- Zastępuje ono pełne środowisko CLR z refaktoryzacją środowiska uruchomieniowego, która przede wszystkim zawiera moduł wyrzucania elementów bezużytecznych. Refaktoryzacja środowiska uruchomieniowego znajduje się w bibliotece o nazwie mrt100_app. dll, która jest lokalna dla aplikacji i ma tylko kilka setek kilobajtów. Jest to możliwe, ponieważ konsolidacja statyczna eliminuje konieczność stosowania wielu usług wykonywanych przez środowisko uruchomieniowe języka wspólnego.

  > [!NOTE]
  > .NET Native używa tego samego modułu wyrzucania elementów bezużytecznych co standardowe środowisko uruchomieniowe języka wspólnego. W .NET Native module wyrzucania elementów bezużytecznych funkcja odzyskiwania pamięci w tle jest domyślnie włączona. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz podstawowe informacje na temat [odzyskiwania pamięci](../../standard/garbage-collection/fundamentals.md).

> [!IMPORTANT]
> .NET Native kompiluje całą aplikację do aplikacji natywnej. Nie zezwala na kompilowanie pojedynczego zestawu zawierającego bibliotekę klas do kodu natywnego, aby można go było wywołać niezależnie od kodu zarządzanego.

Aplikacja powstała w łańcuchu narzędzi .NET Native jest zapisywana w katalogu o nazwie ILC {0}. out w katalogu debugowania lub wersji katalogu projektu. Składa się z następujących plików:

- *\<nazwa_aplikacji >* . exe, plik wykonywalny stub, który po prostu transferuje kontrolę do specjalnego eksportu `Main` w *\<nazwa_aplikacji >* . dll.

- *\<nazwa_aplikacji >* . dll, biblioteka dołączana dynamicznie systemu Windows, która zawiera wszystkie kod aplikacji, a także kod z biblioteki klas .NET Framework oraz wszystkie biblioteki innych firm, na których masz zależność.  Zawiera również kod pomocy technicznej, taki jak kod niezbędny do współpracy z systemem Windows i do serializacji obiektów w aplikacji.

- mrt100_app. dll, Refaktoryzacja środowiska uruchomieniowego, która zapewnia usługi środowiska uruchomieniowego, takie jak odzyskiwanie pamięci.

 Wszystkie zależności są przechwytywane przez manifest APPX aplikacji.  Oprócz plików exe, DLL i mrt100_app. dll, które są powiązane bezpośrednio z pakietem APPX, obejmuje to również dwa pliki:

- msvcr140_app. dll, biblioteka środowiska uruchomieniowego języka C (CRT) używana przez mrt100_app. dll. Jest on dołączony do struktury w pakiecie.

- mrt100. dll. Ta biblioteka zawiera funkcje, które mogą zwiększyć wydajność mrt100_app. dll, chociaż jego nieobecność nie zapobiega działaniu mrt100_app. dll. Jest ładowany z katalogu system32 na komputerze lokalnym, jeśli jest obecny.

Ponieważ łańcuch narzędzi .NET Native łączy kod implementacji w aplikacji tylko wtedy, gdy wie, że aplikacja faktycznie wywołuje ten kod, metadane lub kod implementacji wymagane w następujących scenariuszach mogą nie zostać dołączone do aplikacji:

- Powiela.

- Wywołanie dynamiczne lub z późnym wiązaniem.

- Serializacja i deserializacja.

- Międzyoperacyjność modelu COM.

Jeśli w czasie wykonywania nie ma niezbędnych metadanych lub kodu implementacji, środowisko uruchomieniowe .NET Native zgłasza wyjątek. Można zapobiec tym wyjątkom i upewnić się, że łańcuch narzędzi .NET Native zawiera wymagane metadane i kod implementacji, przy użyciu [pliku dyrektywy środowiska uruchomieniowego](runtime-directives-rd-xml-configuration-file-reference.md), pliku XML, który wyznacza elementy programu, których metadane lub implementacja kod musi być dostępny w czasie wykonywania i przypisuje do nich zasady środowiska uruchomieniowego. Poniżej przedstawiono domyślny plik dyrektywy środowiska uruchomieniowego, który jest dodawany do projektu sklepu Windows, który jest kompilowany przez łańcuch narzędzi .NET Native:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>
```

Dzięki temu wszystkie typy, a także wszystkie ich elementy członkowskie, we wszystkich zestawach w pakiecie aplikacji na potrzeby odbicia i dynamicznego wywoływania. Jednak nie włącza odbicia ani dynamicznej aktywacji typów w zestawach bibliotek klas .NET Framework. W wielu przypadkach jest to odpowiednie.

## <a name="net-native-and-ngen"></a>.NET Native i NGEN

[(Natywny Generator obrazu](../tools/ngen-exe-native-image-generator.md) (Ngen) kompiluje zestawy do kodu natywnego i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Jednak chociaż program NGEN, taki jak .NET Native, generuje kod natywny, różni się od .NET Native w znaczący sposób:

- Jeśli dla określonej metody nie jest dostępny obraz natywny, NGEN powróci do kodu JITing. Oznacza to, że obrazy natywne muszą nadal zawierać metadane i IL w przypadku, gdy NGEN wymaga powrotu do kompilacji JIT. Z kolei .NET Native wytwarza tylko obrazy natywne i nie wraca do kompilacji JIT. W związku z tym należy zachować tylko metadane wymagane dla niektórych scenariuszy odbicia, serializacji i międzyoperacyjności.

- Program NGEN nadal korzysta z pełnego środowiska uruchomieniowego języka wspólnego dla usług, takich jak ładowanie zestawu, komunikacja zdalna, międzyoperacyjność, zarządzanie pamięcią, wyrzucanie elementów bezużytecznych i, w razie potrzeby, kompilacja JIT. W .NET Native wiele z tych usług jest niepotrzebnych (kompilacja JIT) lub są rozwiązywane w czasie kompilacji i zawarte w zestawie aplikacji. Pozostałe usługi, najważniejsze dla których jest wyrzucania elementów bezużytecznych, są uwzględniane w znacznie mniejszym, refaktoryzacjnym środowisku uruchomieniowym o nazwie mrt100_app. dll.

- Obrazy NGEN są bardzo delikatne. Na przykład poprawka lub zmiana do zależności zwykle wymaga ponownego NGEN zestawów, które go używają. Jest to szczególnie prawdziwe w przypadku zestawów systemu w bibliotece klas .NET Framework. Z kolei .NET Native zezwala na obsługę aplikacji niezależnie od siebie.

## <a name="see-also"></a>Zobacz także

- [Składniki samoopisujące się i metadane](../../standard/metadata-and-self-describing-components.md)
- [Wewnątrz .NET Native (wideo Channel 9)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Odbicie i architektura .NET Native](reflection-and-net-native.md)
- [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](net-native-general-troubleshooting.md)
