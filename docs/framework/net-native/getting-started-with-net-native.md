---
title: Wprowadzenie do architektury .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 07882617e7625c07bade85c59116581e16f95121
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-net-native"></a>Wprowadzenie do architektury .NET Native
Czy pisania nową aplikację systemu Windows dla systemu Windows 10 lub w przypadku migracji z istniejącej aplikacji Sklepu Windows, możesz wykonać ten sam zestaw procedur. Aby utworzyć [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji, wykonaj następujące kroki:  
  
1.  [Tworzenie aplikacji systemu Windows platformy Uniwersalnej, przeznaczonego dla systemu Windows 10](#Step1)i testu kompilacje debugowania aplikacji w taki sposób, aby upewnić się, że działa on prawidłowo.  
  
2.  [Obsłużyć dodatkowe obciążenie odbicia i serializacja](#Step2).  
  
3.  [Wdrażanie i testowanie kompilacjami wydania aplikacji](#Step3).  
  
4.  [Ręcznie rozwiązać Brak metadanych](#Step4)i powtórz [krok 3](#Step3) dopóki wszystkie problemy zostały rozwiązane.  
  
> [!NOTE]
>  Podczas migrowania istniejącej aplikacji Sklepu Windows do [!INCLUDE[net_native](../../../includes/net-native-md.md)], należy przejrzeć [migrowanie aplikacji ze Sklepu Windows Your do platformy .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1: Tworzenie i kompilacje debugowania testów aplikacji platformy uniwersalnej systemu Windows  
 Czy są Tworzenie nowej aplikacji lub migracji istniejącej, możesz wykonaj te same czynności, jak w przypadku dowolnej aplikacji systemu Windows.  
  
1.  Tworzenie nowego projektu platformy uniwersalnej systemu Windows w programie Visual Studio przy użyciu szablonu aplikacji uniwersalnych systemu Windows dla języka Visual C# lub Visual Basic. Domyślnie środowisko CoreCLR docelowego wszystkich aplikacji platformy uniwersalnej systemu Windows, a następnie ich kompilacjami wydania są kompilowane przy użyciu platformy .NET Native łańcucha narzędzi.  
  
2.  Należy pamiętać, że niektóre znane problemy ze zgodnością między kompilowanie projektów aplikacji uniwersalnych systemu Windows z użyciem platformy .NET Native łańcucha narzędzi i bez niego. Zapoznaj się [Przewodnik po migracji](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) Aby uzyskać więcej informacji.  
  
 Teraz można napisać kod C# lub Visual Basic [!INCLUDE[net_native](../../../includes/net-native-md.md)] powierzchnia uruchomionym w systemie lokalnym (lub w symulatorze).  
  
> [!IMPORTANT]
>  Podczas opracowywania aplikacji, należy zwrócić uwagę stosowania serializacji lub odbicie w kodzie.  
  
 Kompilacje debugowania są domyślnie kompilacji JIT umożliwia szybkie wdrażanie F5, podczas gdy kompilacjami wydania są kompilowane przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] technologii wstępnej kompilacji. Oznacza to, należy utworzyć i przetestować debugowania kompilacji aplikacji w taki sposób, aby upewnić się, że działają normalnie przed skompilowaniem ich z użyciem platformy .NET Native łańcucha narzędzi.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2: Obsługi dodatkowych odbicia i użycie serializacji  
 Podczas tworzenia pliku dyrektyw środowiska uruchomieniowego Default.rd.xml, jest automatycznie dodawany do projektu. W przypadku tworzenia w języku C#, został znaleziony w projektu **właściwości** folderu. W przypadku tworzenia w języku Visual Basic, został znaleziony w projektu **mój projekt** folderu.  
  
> [!NOTE]
>  Omówienie procesu kompilacji platformy .NET Native podano ogólne informacje o tym, dlaczego jest potrzebny pliku dyrektyw środowiska uruchomieniowego, zobacz [platformy .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Pliku dyrektyw środowiska uruchomieniowego służy do definiowania metadanych, które Twoja aplikacja powinna w czasie wykonywania. W niektórych przypadkach odpowiednie może być domyślna wersja pliku. Jednak niektóre kod, który wykorzystuje serializacji lub odbicia może wymagać dodatkowych wpisów w pliku dyrektyw środowiska uruchomieniowego.  
  
 **Serializacja**  
 Istnieją dwie kategorie serializatorów, a jednocześnie może wymagać dodatkowych wpisów w pliku dyrektyw środowiska uruchomieniowego:  
  
-   Serializatorów oparty na Non odbiciu. Znaleziono w bibliotece klas programu .NET Framework, takich jak serializatorów <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klas, nie należy polegać na podstawie odbicia. Jednak wymaga wygenerowania kodu na podstawie obiektu serializacji lub deserializacji.  Aby uzyskać więcej informacji, zobacz sekcję "Microsoft Serializers" w [serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Serializatorów innych firm. Biblioteki serializacji innych firm, najbardziej typowe którego jest serializator Newtonsoft JSON, są zwykle oparte na odbicie i wprowadzone w *. pliku rd.xml do obsługi obiektu serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz sekcję "Serializatorów innych firm" w [serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Metody, które działają na podstawie odbicia**  
 W niektórych przypadkach użycia odbicie w kodzie nie jest widoczne. Niektóre typowe interfejsów API lub wzorce programowania nie są traktowane jako część odbicia interfejsu API, ale korzystają z odbicia się pomyślnie. Obejmuje to następujące wystąpienia typu i metody konstruowania metod:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> — Metoda  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> i <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metody.  
  
 Aby uzyskać więcej informacji, zobacz [interfejsów API, że działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Nazwy typów, używany w plikach dyrektywy środowiska uruchomieniowego musi być w pełni kwalifikowana. Na przykład plik należy określić "System.String" zamiast "String".  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3: Wdrażanie i testowanie kompilacji wersji aplikacji  
 Po zaktualizowaniu pliku dyrektyw środowiska uruchomieniowego można odbudować i wdrażać kompilacje wersji aplikacji. .NET natywne pliki binarne są umieszczane w katalogu określonym w podkatalogu ILC.out **ścieżki wyjściowej kompilacji** pole tekstowe z projektu **właściwości** okno dialogowe **skompilować**kartę. Pliki binarne, które nie są w tym folderze nie zostały skompilowane z platformy .NET Native. Dokładnie przetestuj aplikację i przetestowania wszystkich scenariuszy, w tym przypadku pewnych scenariuszy awarii, na każdym z jego platformy docelowe.  
  
 Jeśli aplikacja nie działa prawidłowo (szczególnie w przypadku, gdy zgłasza [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątków w czasie wykonywania), postępuj zgodnie z instrukcjami w następnej sekcja, [krok 4: ręcznie rozwiązać Brak metadanych](#Step4). Włączanie wyjątków pierwszej szansy może pomóc w znalezieniu te usterki.  
  
 Gdy przetestowane i debugować debugowania kompilacje aplikacji i masz pewność, że Wyeliminowano [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątki, należy przetestować aplikację jako zoptymalizowane [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji. Aby to zrobić, należy zmienić konfigurację aktywnego projektu z **debugowania** do **wersji**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4: Ręcznie rozwiązać Brak metadanych  
 Najbardziej typowe awarii podłączania z [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie występują na pulpicie jest środowisko uruchomieniowe [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), lub [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku. W niektórych przypadkach brak metadanych można manifestu się w sposób nieprzewidywalny lub nawet w przypadku awarii aplikacji. W tej sekcji omówiono sposób debugowania i rozwiązania tych wyjątków przez dodanie dyrektywy do pliku dyrektyw środowiska uruchomieniowego. Aby uzyskać informacje na temat formatu dyrektyw środowiska uruchomieniowego, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Po dodaniu dyrektyw środowiska uruchomieniowego powinien [wdrażanie i testowanie aplikacji](#Step3) ponownie i rozwiązać wszelkie nowe [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dopóki nie wystąpi żadne wyjątki więcej.  
  
> [!TIP]
>  Określ dyrektyw środowiska uruchomieniowego na wysokim poziomie, aby umożliwić aplikacji pozwala uzyskać odporność na zmiany kodu.  Firma Microsoft zaleca dodanie dyrektyw środowiska uruchomieniowego na poziomy przestrzeń nazw i typ, a nie z poziomu elementu członkowskiego. Należy pamiętać, że mogą być zależności między odporność i większych plików binarnych o wydłużenie czasu kompilacji.  
  
 Podczas adresowania Brak wyjątek metadanych, należy wziąć pod uwagę następujące problemy:  
  
-   Co aplikacja próbuje zrobić przed wyjątek?  
  
    -   Na przykład czy zostało on danych powiązanie, serializacji lub deserializacji danych lub bezpośrednio za pomocą odbicia interfejsu API?  
  
-   Dotyczy to izolowanym, lub czy uważasz, że będziesz występuje ten sam problem, w przypadku innych typów?  
  
    -   Na przykład [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek podczas serializacji typu w modelu obiektu aplikacji.  Jeśli znasz innych typów, które będą serializowane, w tym samym czasie można dodać dyrektyw środowiska uruchomieniowego dla tych typów (lub zawierające je obszary nazw, w zależności od tego, jak kod jest zorganizowana).  
  
-   Można zmodyfikować, kod, aby nie używać odbicia?  
  
    -   Na przykład jest używana kodu `dynamic` — słowo kluczowe, gdy wiadomo, jaki typ oczekiwany?  
  
    -   Kod wywołanie metody, która jest zależna od odbicia, gdy niektóre lepszym jest dostępna?  
  
> [!NOTE]
>  Aby uzyskać dodatkowe informacje na temat obsługi problemów, które wynikają z różnic w odbicie i dostępność metadanych w aplikacjach klasycznych i [!INCLUDE[net_native](../../../includes/net-native-md.md)], zobacz [interfejsów API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Oto kilka przykładów Obsługa wyjątków i inne problemy występujące podczas testowania aplikacji Zobacz:  
  
-   [Przykład: Obsługa wyjątków podczas wiązania danych](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [Wyjątki czasu wykonywania w aplikacjach .NET Native](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [NIB: .NET Native i Konfiguracja](http://msdn.microsoft.com/en-us/7c9bc375-8b87-4c33-bede-72d513e362ec)  
 [Architektura .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md)  
 [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
 [Serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md)  
 [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
