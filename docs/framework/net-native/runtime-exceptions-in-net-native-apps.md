---
title: Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27a2e0906343d115c47230c726efb74cd51d4c93
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049158"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
Ważne jest, aby przetestować kompilacje wydań aplikacji platforma uniwersalna systemu Windows na swoich platformach docelowych, ponieważ konfiguracje debugowania i wydań są całkowicie różne. Domyślnie Konfiguracja debugowania używa środowiska uruchomieniowego .NET Core do kompilowania aplikacji, ale konfiguracja wydania używa .NET Native do kompilowania aplikacji do kodu natywnego.  
  
> [!IMPORTANT]
> Aby uzyskać informacje na temat postępowania z wyjątkami [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , które mogą wystąpić podczas testowania wersji aplikacji, zobacz sekcję "krok 4: Ręcznie Rozwiązuj brakujące metadane: w temacie [wprowadzenie](getting-started-with-net-native.md) , a także informacje dotyczące [odbicia i .NET Native](reflection-and-net-native.md) i [środowiska uruchomieniowego dyrektywy (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Kompilacje debugowania i wydania  
 Gdy Kompilacja debugowania jest wykonywana w środowisku uruchomieniowym .NET Core, nie została skompilowana do kodu natywnego. Dzięki temu wszystkie usługi zwykle dostarczane przez środowisko uruchomieniowe są dostępne dla Twojej aplikacji.  
  
 Z drugiej strony Kompilacja wydania kompiluje się do kodu natywnego dla platform docelowych, usuwa większość zależności od zewnętrznych środowisk uruchomieniowych i bibliotek i intensywnie optymalizuje kod pod kątem maksymalnej wydajności.  
  
 Gdy debugujesz kompilacje wydań, które są kompilowane przy użyciu .NET Native:  
  
- Używasz aparatu debugowania .NET Native, który różni się od normalnych narzędzi debugowania platformy .NET.  
  
- Rozmiar pliku wykonywalnego jest krótszy, jak to możliwe. Jednym ze sposobów, który .NET Native zmniejsza rozmiar pliku wykonywalnego, jest znacznie przycinanie komunikatów o wyjątkach środowiska uruchomieniowego, temat opisany szczegółowo w sekcji [komunikaty o wyjątkach czasu wykonywania](#Messages) .  
  
- Kod jest silnie zoptymalizowany. Oznacza to, że użycie funkcji tworzenia konspektu jest zawsze możliwe. (Odkreślenie przenosi kod z procedur zewnętrznych do procedury wywołującej).   Fakt, że .NET Native zapewnia wyspecjalizowane środowisko uruchomieniowe i implementuje agresywne wywołanie funkcji, która jest wyświetlana podczas debugowania.  Aby uzyskać więcej informacji, zobacz sekcję [stosu wywołań środowiska uruchomieniowego](#CallStack) .  
  
> [!NOTE]
> Można kontrolować, czy kompilacje i wersje kompilacji są kompilowane za pomocą łańcucha narzędzi .NET Native, zaznaczając lub usuwając zaznaczenie pola wyboru **Kompiluj z .NET Native** .   Należy jednak pamiętać, że Sklep Windows zawsze kompiluje wersję produkcyjną aplikacji za pomocą łańcucha narzędzi .NET Native.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Komunikaty o wyjątkach środowiska uruchomieniowego  
 Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie zawiera pełnego tekstu komunikatów o wyjątkach. W związku z tym wyjątki środowiska uruchomieniowego zgłoszone w kompilacjach wydania mogą nie wyświetlać pełnego tekstu komunikatów o wyjątkach. Zamiast tego tekst może składać się z podciągu wraz z linkiem do kolejnych informacji. Na przykład informacje o wyjątku mogą wyglądać następująco:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Jeśli potrzebujesz pełnego komunikatu o wyjątku, zamiast tego Uruchom kompilację debugowania. Na przykład poprzednie informacje o wyjątku z kompilacji wydania mogą pojawić się w następujący sposób w kompilacji debugowania:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Stos wywołań środowiska uruchomieniowego  
 Ze względu na niepodkreślanie i inne optymalizacje stos wywołań wyświetlany przez aplikację skompilowaną przez łańcuch narzędzi .NET Native może nie pomóc w jasno określić ścieżki do wyjątku czasu wykonywania.  
  
 Aby uzyskać pełny stos, zamiast tego Uruchom kompilację debugowania.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie .NET Native uniwersalnych aplikacji systemu Windows](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Wprowadzenie](getting-started-with-net-native.md)
