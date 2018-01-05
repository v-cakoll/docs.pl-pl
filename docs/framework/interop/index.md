---
title: "Współdziałanie z kodem niezarządzanym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f475877bcb7a794d1a58ef9202735e016363678b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym
.NET Framework zamienia interakcji z COM składników, COM + usług, bibliotek typu zewnętrznego i wiele usług systemu operacyjnego. Typy danych, podpisy metod i mechanizmy obsługi błędów różnić modele obiektów zarządzanych i niezarządzanych. Aby uprościć współdziałanie między składników .NET Framework i kodu niezarządzanego i ścieżki migracji do jej obsługi ułatwiają, środowisko uruchomieniowe języka wspólnego zawiera od klientów i serwerów różnice w tych modeli obiektów.  
  
 Kod, który wykonuje pod kontrolą środowiska uruchomieniowego jest wywoływana kodu zarządzanego. Z drugiej strony kod uruchamiany poza środowisko wykonawcze jest nazywany kodu niezarządzanego. Składniki modelu COM, interfejsy ActiveX i funkcji Win32 API są przykłady kodu niezarządzanego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Współdziałanie z kodem niezarządzanym — tematy porad](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 Zawiera łącza do wszystkich — tematy porad znajdującego się w dokumentacji koncepcyjnej na współdziałanie z kodem niezarządzanym.  
  
 [Udostępnianie składników COM programowi .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 Informacje dotyczące używania składniki COM w aplikacjach .NET Framework.  
  
 [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Informacje dotyczące używania składników .NET Framework z aplikacjami COM.  
  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.  
  
 [Zagadnienia dotyczące projektowania dla współdziałanie](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 Porady dotyczące pisania zintegrowane składników COM.  
  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)  
 Opisuje, przekazywanie do wywoływania platformy i COM interop.  
  
 [Instrukcje: Mapowanie wyników HRESULT i wyjątków](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 Opisuje mapowanie między wyjątki i wyników HRESULT.  
  
 [Współdziałanie za pomocą typów ogólnych](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 Określa zachowanie typów ogólnych w modelu COM interop.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Współdziałanie COM zaawansowane](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Zawiera łącza do dodatkowych informacji o włączenie składniki modelu COM aplikacji .NET Framework.
