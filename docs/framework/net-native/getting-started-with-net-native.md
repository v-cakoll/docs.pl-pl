---
title: Wprowadzenie do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41679d4041a6a5a7b9b71a451a083c539d6b4c7b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090256"
---
# <a name="getting-started-with-net-native"></a>Wprowadzenie do architektury .NET Native
Czy podczas pisania nowych aplikacji Windows dla systemu Windows 10 jest przeprowadzana migracja istniejącej aplikacji Windows Store, możesz wykonać ten sam zestaw procedur. Aby utworzyć [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji, wykonaj następujące kroki:  
  
1.  [Tworzenie aplikacji uniwersalnych platformy Windows (UWP), który jest przeznaczony dla systemu Windows 10](#Step1), tworzenie i testowanie kompilacji debugowania aplikacji w taki sposób, aby upewnić się, że działa on prawidłowo.  
  
2.  [Obsługa dodatkowe użycie odbicia i serializacja](#Step2).  
  
3.  [Wdrażanie i testowanie kompilacji wydania aplikacji](#Step3).  
  
4.  [Ręczne rozwiązywanie Brak metadanych](#Step4)i powtórz [kroku 3](#Step3) dopóki wszystkie problemy są rozwiązywane.  
  
> [!NOTE]
>  Jeśli migrujesz istniejącą aplikację Windows Store w celu [!INCLUDE[net_native](../../../includes/net-native-md.md)], należy przejrzeć [Migrowanie Your Windows Store aplikacji platformy .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1: Tworzenie i debugowania testowego kompilacji aplikacji platformy uniwersalnej systemu Windows  
 Czy tworzysz nową aplikację lub Migrowanie istniejącą, wykonaj się tego samego procesu jak w przypadku dowolnej aplikacji Windows.  
  
1.  Utwórz nowy projekt platformy uniwersalnej systemu Windows w programie Visual Studio za pomocą szablonu aplikacji Universal Windows dla języka Visual C# lub Visual Basic. Domyślnie wszystkie aplikacje platformy uniwersalnej systemu Windows docelowe oprogramowania CoreCLR i ich kompilacji wydania są kompilowane przy użyciu platformy .NET Native łańcucha narzędzi.  
  
2.  Należy pamiętać, że istnieją niektóre znane problemy ze zgodnością między kompilowanie projektów aplikacji platformy uniwersalnej systemu Windows przy użyciu platformy .NET Native łańcucha narzędzi i bez niego. Zapoznaj się [Przewodnik po migracji](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) Aby uzyskać więcej informacji.  
  
 Teraz można napisać kod C# lub Visual Basic [!INCLUDE[net_native](../../../includes/net-native-md.md)] powierzchnia, która jest uruchamiana w systemie lokalnym (lub w symulatorze).  
  
> [!IMPORTANT]
>  Podczas opracowywania aplikacji, należy pamiętać, użytkowania serializacji lub odbicia w kodzie.  
  
 Domyślnie jest kompilowany dokładnie na czas umożliwiające szybkie wdrożenie F5, podczas kompilacji wydania są kompilowane przy użyciu kompilacji do debugowania [!INCLUDE[net_native](../../../includes/net-native-md.md)] technologia wstępnej kompilacji. Oznacza to, należy tworzenia i testowania debugowania kompilacji aplikacji w taki sposób, aby upewnić się, że działają normalnie przed skompilowaniem je przy użyciu platformy .NET Native łańcucha narzędzi.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2: Obsługa dodatkowych odbicia i użycia serializacji  
 Plik dyrektywy środowiska uruchomieniowego, Default.rd.xml, jest automatycznie dodawane do projektu podczas jego tworzenia. W przypadku tworzenia w języku C# zostanie znaleziony w twoim projekcie **właściwości** folderu. W przypadku tworzenia w języku Visual Basic, zostanie znaleziony w twoim projekcie **mój projekt** folderu.  
  
> [!NOTE]
>  Omówienie procesu kompilacji platformy .NET Native podano ogólne informacje o tym, dlaczego jest potrzebny plik dyrektywy środowiska uruchomieniowego, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Plik dyrektywy środowiska uruchomieniowego jest używany do definiowania metadanych, które Twoja aplikacja wymaga w czasie wykonywania. W niektórych przypadkach domyślna wersja pliku może być odpowiednie. Jednak niektóre kod, który opiera się na serializacji lub odbicia mogą być potrzebne dodatkowe pozycje w pliku dyrektyw środowiska uruchomieniowego.  
  
 **Serializacja**  
 Istnieją dwie kategorie serializatory, i może wymagać dodatkowe pozycje w pliku dyrektyw środowiska uruchomieniowego:  
  
-   Odbicie inne niż oparte serializatory. Serializatory znalezione w bibliotece klas programu .NET Framework, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy, nie należy polegać na podstawie odbicia. Jednak wymagać można wygenerować kodu na podstawie obiektu serializacji lub deserializacji.  Aby uzyskać więcej informacji, zobacz sekcję "Microsoft Serializers" w [serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Serializatory innych firm. Biblioteki innych firm serializacji, najczęściej z nich jest serializator Newtonsoft JSON, są zazwyczaj oparte na odbicia i wprowadzone w *. rd.xml na plik obiektów serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz sekcję "Serializatory innych firm" w [serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Metody, które działają na podstawie odbicia**  
 W niektórych przypadkach użycie odbicia w kodzie nie jest oczywisty. Niektóre typowe interfejsów API lub wzorców programistycznych nie są traktowane jako część interfejs API odbicia, ale działają na podstawie odbicia, aby pomyślnie wykonać. Obejmuje to następujące wystąpienia typu i metody tworzenia metody:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> — Metoda  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> i <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metody.  
  
 Aby uzyskać więcej informacji, zobacz [interfejsów API, czy działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Nazwy typów, używany w plikach dyrektywy środowiska uruchomieniowego musi być w pełni kwalifikowana. Na przykład plik należy określić "System.String" zamiast "String".  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3: Wdrażanie i testowanie kompilacji wydania aplikacji  
 Po zaktualizowaniu pliku dyrektyw środowiska uruchomieniowego, można ponownie skompilować i wdrażanie kompilacji wydania aplikacji. .NET native pliki binarne są umieszczane w podkatalogu ILC.out w katalogu wskazanym na **ścieżkę wyjściową kompilacji** pole tekstowe projektu **właściwości** okno dialogowe **skompilować**kartę. Jeszcze nie zostały skompilowane pliki binarne, które nie znajdują się w tym folderze z architekturą .NET Native. Dokładnie przetestuj aplikację i przetestować wszystkie scenariusze, w tym scenariuszy awarii, na każdym z jego platform docelowych.  
  
 Jeśli aplikacja nie działa prawidłowo (zwłaszcza w przypadkach, w którym wyniku weryfikacji zgłasza wyjątek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątków w czasie wykonywania), postępuj zgodnie z instrukcjami w ciągu następnych sekcja [krok 4: ręcznie rozwiązać Brak metadanych](#Step4). Włączanie wyjątki pierwszej szansy może pomóc w znalezieniu tych błędów.  
  
 Kiedy został przetestowany i debugować debugowania kompilacji aplikacji i masz pewność, że zostały wyeliminowane [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątki, należy przetestować aplikację jako zoptymalizowane [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji. Aby to zrobić, należy zmienić konfigurację aktywnego projektu z **debugowania** do **wersji**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4: Ręcznie rozwiązać Brak metadanych  
 Najbardziej typowych błędów, którymi spotkasz się za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie występują na pulpicie to środowisko uruchomieniowe [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), lub [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku. W niektórych przypadkach braku metadanych można objawiać nieprzewidywalne zachowanie lub nawet w przypadku błędów aplikacji. W tej sekcji omówiono sposób debugowania i rozpoznania tych wyjątków, dodając dyrektywy do pliku dyrektyw środowiska uruchomieniowego. Aby uzyskać informacje o formacie dyrektyw środowiska uruchomieniowego, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Po dodaniu dyrektywy środowiska uruchomieniowego należy [wdrażania i testowania aplikacji](#Step3) ponownie i rozpoznać żadnej nowe [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dopóki nie wystąpią żadne wyjątki więcej.  
  
> [!TIP]
>  Określ dyrektywy środowiska uruchomieniowego na wysokim poziomie, aby umożliwić zarządzanie aplikacją być odporne na zmiany w kodzie.  Zalecamy dodanie dyrektywy środowiska uruchomieniowego na poziomy przestrzeń nazw i typ, a nie na poziomie elementu członkowskiego. Należy pamiętać, że może być zależność między odporność i większe pliki binarne o wydłużenie czasu kompilacji.  
  
 Podczas adresowania Brak wyjątek metadanych, należy wziąć pod uwagę te problemy:  
  
-   Co aplikacja próbuje wykonać przed wystąpieniem wyjątku?  
  
    -   Na przykład był data binding, serializacji lub deserializacji danych lub bezpośrednio przy użyciu interfejs API odbicia?  
  
-   Jest to przypadek w izolowanym, lub czy uważasz, że będziesz napotkasz ten sam problem w przypadku innych typów?  
  
    -   Na przykład [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek jest zgłaszany, gdy serializacji typu w modelu obiektu aplikacji.  Jeśli znasz inne typy, które będą serializowane, możesz dodać dyrektywy środowiska uruchomieniowego dla tych typów (lub zawierające je obszary nazw, w zależności od tego, jak kod jest zorganizowana), w tym samym czasie.  
  
-   Dlatego nie korzysta odbicia możesz przepisania kodu?  
  
    -   Na przykład, czy kod `dynamic` — słowo kluczowe, gdy wiesz, jaki typ można oczekiwać?  
  
    -   Kod, wywołać metodę, która jest zależna od odbicia, gdy niektóre lepszą alternatywą jest dostępny?  
  
> [!NOTE]
>  Aby uzyskać dodatkowe informacje na temat obsługi problemów, które wynikają z różnic w odbiciu oraz dostępność metadanych w aplikacjach klasycznych i [!INCLUDE[net_native](../../../includes/net-native-md.md)], zobacz [interfejsów API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Aby uzyskać kilka przykładów Obsługa wyjątków i inne problemy występujące podczas testowania aplikacji Zobacz:  
  
-   [Przykład: Obsługa wyjątków podczas wiązania danych](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [Wyjątki czasu wykonywania w aplikacjach .NET Native](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [NIB: .NET Native instalacji i konfiguracji](https://msdn.microsoft.com/library/7c9bc375-8b87-4c33-bede-72d513e362ec)  
 [Architektura .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md)  
 [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
 [Serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md)  
 [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
