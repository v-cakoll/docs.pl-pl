---
title: Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e07c41d398c0792094b4481a38c69b2ba73004
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208283"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
Jest ważne przetestować kompilacji wydania aplikacji Universal Windows Platform na ich platformach docelowych, ponieważ konfiguracji debug i release całkowicie różnią się. Domyślnie korzysta z konfiguracji debugowania środowiska uruchomieniowego .NET Core do kompilowania aplikacji, ale konfiguracja wydania używa platformy .NET Native do kompilowania aplikacji do kodu macierzystego.  
  
> [!IMPORTANT]
>  Aby uzyskać informacje w sprawach związanych z [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, które użytkownik może Podczas testowania wersji aplikacji, zobacz "krok 4: Ręcznie rozwiązać Brak metadanych: w [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md) tematu, a także [odbicia i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) i [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Kompilacje debugowania i wydania  
 Jeśli kompilacja debugowania jest wykonywana względem czasu wykonywania platformy .NET Core, nie został wcześniej skompilowany na kod natywny. To sprawia, że wszystkie usługi, zazwyczaj dostarczane przez środowisko uruchomieniowe dostępna dla aplikacji.  
  
 Z drugiej strony kompilację wydania kompiluje do kodu natywnego dla swojej platformy docelowe, usuwa większość zależności zewnętrznych środowisk uruchomieniowych i bibliotek i intensywnie optymalizuje kod, aby osiągnąć najwyższą wydajność.  
  
 Podczas debugowania kompilacji wydania, które są kompilowane przy użyciu platformy .NET Native:  
  
-   Możesz użyć platformy .NET Native aparat debugowania, który różni się od normalnych .NET, narzędzia debugowania.  
  
-   Rozmiar plik wykonywalny zmniejsza się w miarę możliwości. Jednym ze sposobów .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinania komunikaty wyjątku środowiska uruchomieniowego, w temacie omówiono bardziej szczegółowo w [komunikaty o wyjątkach środowiska uruchomieniowego](#Messages) sekcji.  
  
-   Twój kod intensywnie jest zoptymalizowany. Oznacza to, że wbudowanie jest używana zawsze, gdy jest to możliwe. (Wbudowanie przenosi kod z procedur zewnętrznych do wywoływania procedury.)   Fakt, że .NET Native udostępnia wyspecjalizowane środowiska uruchomieniowego i implementuje agresywne wbudowanie wpływa na stos wywołań, który jest wyświetlany podczas debugowania.  Aby uzyskać więcej informacji, zobacz [stosu środowiska uruchomieniowego](#CallStack) sekcji.  
  
> [!NOTE]
>  Można kontrolować, czy debug i release kompilacje są kompilowane przy użyciu łańcucha narzędzi .NET Native przez zaznaczenie lub usunięcie zaznaczenia **kompilacji z łańcucha narzędzi .NET Native** pole.   Należy jednak pamiętać, że Store Windows zawsze zostanie skompilowany w wersję produkcyjną aplikacji przy użyciu platformy .NET Native łańcucha narzędzi.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Komunikaty o wyjątkach środowiska uruchomieniowego  
 Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie obejmuje pełny tekst komunikaty o wyjątkach. W rezultacie wyjątki środowiska uruchomieniowego zgłoszony w wydawanych wersjach mogą nie wyświetlać pełny tekst komunikaty o wyjątkach. Zamiast tego tekstu może składać się podciągu wraz z linkiem do wykonania, aby uzyskać więcej informacji. Na przykład informacje o wyjątku może pojawić się jako:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Jeśli potrzebujesz komunikat o wyjątku pełną, należy uruchomić kompilację debugowania. Na przykład poprzednie informacje o wyjątku z kompilacji wydania może wyglądać następująco w kompilacji debugowania:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Stos wywołań środowiska uruchomieniowego  
 Ze względu na wbudowanie i inne optymalizacje stos wywołań, wyświetlany przez aplikację, skompilowany przez łańcuch narzędzi .NET Native nie mogą pomóc Ci celu jednoznacznego zidentyfikowania ścieżkę do wyjątku czasu wykonywania.  
  
 Aby uzyskać pełny stos, należy zamiast tego należy uruchomić z kompilacji debugowania.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie aplikacji Universal Windows natywnych platformy .NET](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
