---
title: Otoki COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b633239be85a66c5bba54132c3732357967eb177
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182939"
---
# <a name="com-wrappers"></a>Otoki COM
COM różni się od modelu obiektów programu .NET Framework na kilka sposobów ważne:  
  
-   Klienci obiektów COM musi zarządzać okresem istnienia tych obiektów; środowisko uruchomieniowe języka wspólnego zarządza czasem istnienia obiektów w swoim środowisku.  
  
-   Klienci obiektów COM Dowiedz się, czy usługa jest dostępna, żądając interfejs, który zawiera tę usługę i powrót wskaźnika interfejsu, czy nie. Klienci obiektów platformy .NET można uzyskać opisu funkcji obiektu przy użyciu odbicia.  
  
-   Obiekty sieci znajdują się w pamięci zarządzane przez środowisko wykonawcze .NET Framework. Środowisko wykonawcze można poruszać obiektów w pamięci, ze względu na wydajność i zaktualizuj wszystkie odwołania do obiektów, które przenosi. Niezarządzanych klientów, uzyskaniu wskaźnik do obiektu, zależą od obiektu, aby pozostać w tej samej lokalizacji. Ci klienci mają żaden mechanizm służący do radzenia sobie z obiektem, którego lokalizacja nie zostanie usunięty.  
  
 Aby wyeliminować te różnice, środowisko wykonawcze zapewnia klas otoki się klientów zarządzanych i niezarządzanych, wydaje się, że wywołania obiektów w ramach odpowiednio ich środowiska. Zawsze, gdy zarządzanego klienta wywołuje metodę dla obiektów COM, środowisko uruchomieniowe tworzy [wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md) (RCW). RCW abstrakcyjna różnice między mechanizmów odwołania zarządzane i niezarządzane, między innymi. Środowisko uruchomieniowe wzrasta, powstaje [wywoływana otoka COM](com-callable-wrapper.md) (CCW), aby cofnąć ten proces włączania klient modelu COM bezproblemowo wywołania metody wobec obiektu .NET. Jak pokazano na poniższej ilustracji, perspektywy kod wywołujący Określa, która klasa otoki, środowisko uruchomieniowe tworzy.  
  
 ![Przegląd otoki COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 W większości przypadków standard RCW lub CCW generowane przez środowisko wykonawcze zapewnia odpowiednie kierowanie wywołań, które przekraczają granicę między COM i .NET Framework. Za pomocą atrybutów niestandardowych, można opcjonalnie dostosować sposób, środowisko uruchomieniowe reprezentuje kodem zarządzanym i niezarządzanym.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)
- [Wywoływana otoka COM](com-callable-wrapper.md)
- [Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Instrukcje: Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))
