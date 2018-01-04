---
title: "Wyjątki czasu wykonywania w natywnych aplikacji .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea4901eca45a4b02e3eeb9fa8a3ac2a9efa3484
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Wyjątki czasu wykonywania w natywnych aplikacji .NET
Należy koniecznie test kompilacjami wydania aplikacji platformy uniwersalnej systemu Windows na ich platformach docelowych, ponieważ są całkowicie różne konfiguracje debug i release. Domyślnie korzysta z konfiguracji debugowania środowiska uruchomieniowego .NET Core do skompilowania aplikacji, ale konfiguracja wydania używają platformy .NET Native skompilować aplikację do kodu natywnego.  
  
> [!IMPORTANT]
>  Aby uzyskać informacje o obsłudze [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, które możesz Podczas testowania wersji aplikacji, zobacz "krok 4: ręcznie rozwiązać Brak metadanych: w [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md) tematu, jak również [odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) i [ Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Kompilacje debugowania i wydania  
 Podczas kompilacji debugowania dla środowiska uruchomieniowego .NET Core, nie ma została skompilowana do kodu natywnego. Spowoduje to uruchomienie wszystkich usług, zwykle dostarczonym w czasie wykonywania, dostępne dla aplikacji.  
  
 Z drugiej strony kompilacji wydania kompiluje się do kodu natywnego dla jego platformy docelowe, powoduje usunięcie większości zależności zewnętrznych środowisk uruchomieniowych i bibliotek i silnie optymalizuje kod dla maksymalnej wydajności.  
  
 Podczas debugowania kompilacjami wydania, które są kompilowane przy użyciu platformy .NET Native:  
  
-   Używasz platformy .NET Native aparat debugowania, który różni się od normalnego narzędzia debugowania środowiska .NET.  
  
-   Rozmiar pliku wykonywalnego zmniejsza się w miarę możliwości. Jednym ze sposobów platformy .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinanie komunikaty o wyjątkach środowiska uruchomieniowego, temacie omówiono bardziej szczegółowo w [komunikaty o wyjątkach środowiska uruchomieniowego](#Messages) sekcji.  
  
-   Kod silnie jest zoptymalizowany. Oznacza to, że ze śródwierszowaniem jest używany, gdy jest to możliwe. (Ze Śródwierszowaniem przenosi kodu z zewnętrznej procedury do wywoływania procedury.)   Fakt, że platforma .NET Native zawiera specjalne środowiska uruchomieniowego i implementuje agresywne ze śródwierszowaniem wpływa na stos wywołań, który jest wyświetlany podczas debugowania.  Aby uzyskać więcej informacji, zobacz [stosu wywołań środowiska uruchomieniowego](#CallStack) sekcji.  
  
> [!NOTE]
>  Można kontrolować, czy kompilacji debug i release są kompilowane przy użyciu platformy .NET Native łańcucha narzędzi przez zaznaczenie lub usunięcie zaznaczenia **Kompiluj z użyciem łańcucha narzędzi dla platformy .NET Native** pole.   Należy jednak pamiętać, że Sklep Windows zawsze zostanie skompilowany wersji produkcyjnej aplikacji z użyciem platformy .NET Native łańcucha narzędzi.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Komunikaty o wyjątkach środowiska wykonawczego  
 Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, platformy .NET Native nie obejmuje pełny tekst komunikaty o wyjątku. W związku z tym obsługi wyjątków zgłoszonych w kompilacjach wydania nie może być wyświetlany pełny tekst komunikaty o wyjątku. Zamiast tego tekst może zawierać podciąg wraz z linkiem, które należy wykonać, aby uzyskać więcej informacji. Na przykład informacje o wyjątku może pojawić się jako:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Komunikat o wyjątku pełnej, należy należy uruchomić z kompilacji debugowania. Na przykład informacje o poprzednich wyjątku z kompilacji wydania mogą wyglądać następująco w kompilacji debugowania:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Stos wywołań środowiska wykonawczego  
 Z powodu optymalizacji ze śródwierszowaniem i innych stos wywołań, wyświetlane przez aplikację skompilowane przez platformę .NET Native łańcucha narzędzi może nie pomóc w celu jednoznacznego zidentyfikowania ścieżkę do wyjątek czasu wykonywania.  
  
 Aby uzyskać pełne stosu, należy uruchomić kompilacji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowania .NET Native uniwersalnych aplikacji systemu Windows](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
