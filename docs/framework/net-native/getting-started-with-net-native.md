---
title: Wprowadzenie do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de887f73a5cc3968dda7e0e4dd14493883485d2b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049736"
---
# <a name="getting-started-with-net-native"></a>Wprowadzenie do architektury .NET Native

Niezależnie od tego, czy piszesz nową aplikację systemu Windows dla systemu Windows 10, czy przeprowadzasz migrację istniejącej aplikacji ze sklepu Windows, możesz wykonać ten sam zestaw procedur. Aby utworzyć aplikację .NET Native, wykonaj następujące kroki:

1. [Utwórz aplikację platforma uniwersalna systemu Windows (platformy UWP), która jest przeznaczona dla systemu Windows 10](#Step1), i przetestuj kompilacje debugowania aplikacji, aby upewnić się, że działa prawidłowo.

2. [Obsługa dodatkowego odbicia i użycia serializacji](#Step2).

3. [Wdróż i przetestuj kompilacje wydania aplikacji](#Step3).

4. [Ręcznie Rozwiąż brakujące metadane](#Step4)i powtórz [krok 3](#Step3) , dopóki wszystkie problemy nie zostaną rozwiązane.

> [!NOTE]
> Jeśli migrujesz istniejącą aplikację ze sklepu Windows do .NET Native, pamiętaj o [przejściu do sekcji Migrowanie aplikacji ze sklepu Windows do .NET Native](migrating-your-windows-store-app-to-net-native.md).

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1. Opracowywanie i testowanie kompilacji debugowania aplikacji platformy UWP

Bez względu na to, czy tworzysz nową aplikację, czy migrujesz istniejącą, postępuj zgodnie z tym samym procesem co w przypadku dowolnej aplikacji systemu Windows.

1. Utwórz nowy projekt platformy UWP w programie Visual Studio przy użyciu szablonu uniwersalnej aplikacji systemu Windows dla C# wizualizacji lub Visual Basic. Domyślnie wszystkie aplikacje platformy UWP są przeznaczone dla CoreCLR i ich kompilacje wydania są kompilowane za pomocą łańcucha narzędzi .NET Native.

2. Należy zauważyć, że istnieją znane problemy ze zgodnością między kompilowaniem projektów aplikacji platformy UWP za pomocą łańcucha narzędzi .NET Native i bez niego. Aby uzyskać więcej informacji, zapoznaj się z [przewodnikiem migracji](migrating-your-windows-store-app-to-net-native.md) .

Można teraz napisać C# lub Visual Basic kod względem obszaru .NET Native powierzchni, który działa w systemie lokalnym (lub w symulatorze).

> [!IMPORTANT]
> Podczas opracowywania aplikacji Zwróć uwagę na użycie serializacji lub odbicia w kodzie.

Domyślnie kompilacje debugowania są kompilowane w trybie JIT, aby umożliwić szybkie wdrażanie, podczas gdy kompilacje wydania są kompilowane przy użyciu technologii prekompilowania .NET Native. Oznacza to, że należy skompilować i przetestować kompilacje debugowania aplikacji, aby upewnić się, że działają one normalnie przed skompilowaniem przy użyciu łańcucha narzędzi .NET Native.

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2. Obsługa dodatkowego odbicia i użycia serializacji

Plik dyrektywy środowiska uruchomieniowego, default. Rd. XML, jest automatycznie dodawany do projektu podczas jego tworzenia. W przypadku tworzenia aplikacji C#w programie zostanie ona znaleziona w folderze **Właściwości** projektu. Jeśli tworzysz program w Visual Basic, zostanie on znaleziony w folderze **mój projekt** projektu.

> [!NOTE]
> Aby zapoznać się z omówieniem procesu kompilacji .NET Native, który zawiera informacje o tym, dlaczego plik dyrektywy środowiska uruchomieniowego jest zbędny, zobacz [.NET Native i kompilacja](net-native-and-compilation.md).

Plik dyrektywy środowiska uruchomieniowego służy do definiowania metadanych wymaganych przez aplikację w czasie wykonywania. W niektórych przypadkach domyślna wersja pliku może być odpowiednia. Jednak jakiś kod, który opiera się na serializacji lub odbicie może wymagać dodatkowych wpisów w pliku dyrektywy środowiska uruchomieniowego.

**Serializacja**

Istnieją dwie kategorie serializatorów, które mogą wymagać dodatkowych wpisów w pliku dyrektywy środowiska uruchomieniowego:

- Serializatory na podstawie nieodbicia. Serializatory Znalezione w bibliotece klas .NET Framework, takie jak <xref:System.Runtime.Serialization.DataContractSerializer>klasy, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> , nie polegają na odbiciu. Jednak wymagają one, aby kod został wygenerowany na podstawie obiektu, który ma być serializowany lub deserializowany.  Aby uzyskać więcej informacji, zobacz sekcję "serializatory firmy Microsoft" w temacie [serializacji i metadanych](serialization-and-metadata.md).

- Serializatory innych firm. Biblioteki serializacji innych firm, najczęściej typowe dla serializatora JSON Newtonsoft, są zwykle oparte na odbiciach i wymagają wpisów w \*pliku Rd. XML do obsługi serializacji obiektów i deserializacji. Aby uzyskać więcej informacji, zobacz sekcję "serializatory innych firm" w temacie [serializacji i metadanych](serialization-and-metadata.md).

**Metody, które opierają się na odbiciu**

W niektórych przypadkach użycie odbicia w kodzie nie jest oczywiste. Niektóre typowe interfejsy API lub wzorce programowania nie są uważane za część interfejsu API odbicia, ale polegają na pomyślnym wykonaniu odbicia. Obejmuje to następujące typy tworzenia wystąpień i metod konstrukcji metody:

- <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Metoda

- Metody <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> i<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>

- <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metoda.

Aby uzyskać więcej informacji, zobacz [interfejsy API, które opierają się na odbiciu](apis-that-rely-on-reflection.md).

> [!NOTE]
> Nazwy typów używane w plikach dyrektywy środowiska uruchomieniowego muszą być w pełni kwalifikowane. Na przykład plik musi określać "System. String" zamiast "String".

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3. Wdróż i przetestuj kompilacje wydania aplikacji

Po zaktualizowaniu pliku dyrektywy środowiska uruchomieniowego można skompilować i wdrożyć Kompilacje wersji aplikacji. .NET Native pliki binarne są umieszczane w podkatalogu ILC {0}. out katalogu określonego w polu tekstowym **kompilacja ścieżki wyjściowej** w oknie dialogowym **Właściwości** projektu, karta **kompilacja** . Pliki binarne, które nie znajdują się w tym folderze, nie zostały skompilowane przy użyciu .NET Native. Dokładnie Przetestuj swoją aplikację i przetestuj wszystkie scenariusze, w tym scenariusze awarii, na każdej platformie docelowej.

Jeśli aplikacja nie działa prawidłowo (zwłaszcza w przypadkach, gdy w czasie wykonywania zgłasza wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) lub [MissingInteropDataException](missinginteropdataexception-class-net-native.md) ), postępuj zgodnie z instrukcjami w następnej sekcji, [krok 4: Ręcznie Rozwiąż brakujące metadane](#Step4). Włączenie wyjątków pierwszej szansy może pomóc w znalezieniu tych błędów.

Po przetestowaniu i debugowaniu kompilacji debugowania aplikacji i pewności, że zostały wyeliminowane wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md) i [MissingInteropDataException](missinginteropdataexception-class-net-native.md) , należy przetestować aplikację jako zoptymalizowaną .NET Native aplikację. W tym celu Zmień konfigurację aktywnego projektu z **Debuguj** do **Release**.

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4. Ręcznie Rozwiązuj brakujące metadane

Najbardziej typowym błędem napotkanym przez .NET Native, które nie występują na pulpicie, jest wyjątek czasu wykonywania [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)lub [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . W niektórych przypadkach Brak metadanych może być manifestem w nieprzewidywalny sposób lub nawet w przypadku awarii aplikacji. W tej sekcji omówiono, jak można debugować i rozwiązywać te wyjątki, dodając dyrektywy do pliku dyrektywy środowiska uruchomieniowego. Aby uzyskać informacje o formacie dyrektywy środowiska uruchomieniowego, zobacz [Dokumentacja pliku konfiguracji dyrektywy środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md). Po dodaniu dyrektyw środowiska uruchomieniowego należy ponownie [wdrożyć i przetestować aplikację](#Step3) oraz rozwiązać wszelkie nowe wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) do momentu nie występuje więcej wyjątków.

> [!TIP]
> Określ dyrektywy środowiska uruchomieniowego na wysokim poziomie, aby umożliwić odporność aplikacji na zmiany kodu.  Zalecamy dodanie dyrektyw środowiska uruchomieniowego w przestrzeni nazw i na poziomach typu, a nie na poziomie elementu członkowskiego. Należy pamiętać, że może istnieć kompromis między odpornością a większymi plikami binarnymi o dłuższym czasie kompilacji.

W przypadku rozwiązywania brakującego wyjątku metadanych należy wziąć pod uwagę następujące problemy:

- Co aplikacja próbuje wykonać przed wyjątkiem?

  - Na przykład czy dane były powiązane z danymi, serializacja lub deserializacji danych lub bezpośrednio za pomocą interfejsu API odbicia?

- Czy jest to izolowany przypadek, czy uważasz, że ten sam problem występuje w przypadku innych typów?

  - Na przykład wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) jest generowany podczas serializowania typu w modelu obiektów aplikacji.  Jeśli wiesz inne typy, które będą serializowane, możesz dodać dyrektywy środowiska uruchomieniowego dla tych typów (lub dla zawierających ich przestrzeni nazw, w zależności od tego, jak dobrze jest zorganizowany kod).

- Czy można ponownie napisać kod, aby nie używał odbicia?

  - Na przykład, czy kod używa słowa kluczowego, `dynamic` gdy wiesz, jakiego typu oczekiwać?

  - Czy kod wywołuje metodę, która zależy od odbicia, gdy jest dostępny jakiś lepszy alternatywa?

> [!NOTE]
> Aby uzyskać dodatkowe informacje na temat obsługi problemów, które wynikają z różnic w odbiciu i dostępności metadanych w aplikacjach klasycznych i .NET Native, zobacz [interfejsy API, które opierają się na odbiciu](apis-that-rely-on-reflection.md).

Aby zapoznać się z konkretnymi przykładami obsługi wyjątków i innych problemów, które występują podczas testowania aplikacji, zobacz:

- [Przykład: Obsługa wyjątków podczas wiązania danych](example-handling-exceptions-when-binding-data.md)

- [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](example-troubleshooting-dynamic-programming.md)

- [Wyjątki czasu wykonywania w aplikacjach .NET Native](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [.NET Native instalacji i konfiguracji](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [Architektura .NET Native i kompilacja](net-native-and-compilation.md)
- [Odbicie i architektura .NET Native](reflection-and-net-native.md)
- [Interfejsy API, które działają na podstawie odbicia](apis-that-rely-on-reflection.md)
- [Serializacja i metadane](serialization-and-metadata.md)
- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](migrating-your-windows-store-app-to-net-native.md)
