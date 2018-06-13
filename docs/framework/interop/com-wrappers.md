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
ms.openlocfilehash: 57483f099bb71a1ab685cedf148d4343c12983dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390526"
---
# <a name="com-wrappers"></a>Otoki COM
COM różni się od modelu obiektów programu .NET Framework w kilka sposobów:  
  
-   Klienci obiektów COM należy zarządzać okres istnienia tych obiektów; środowisko uruchomieniowe języka wspólnego zarządza czasem istnienia obiektów w ich środowisku.  
  
-   Klienci obiektów COM wykrywa, czy usługa jest dostępna, żądając interfejs, który udostępnia usługi i odzyskać wskaźnika interfejsu, czy nie. Klienci obiektów .NET mogą uzyskiwać opisu funkcji obiektu za pomocą odbicia.  
  
-   NET obiekty znajdują się w pamięci, zarządzanych przez środowiska wykonawczego .NET Framework. Poruszanie obiektów w pamięci, ze względu na wydajność i aktualizować wszystkie odwołania do obiektów, które powoduje przeniesienie można środowiska wykonawczego. Klienci Niezarządzani po otrzymaniu wskaźnika do obiektu, zależą od obiektu ma pozostać w tej samej lokalizacji. Ci klienci mają mechanizm zajmujących się obiekt, którego lokalizacja nie jest stały.  
  
 Aby wyeliminować te różnice, środowiska uruchomieniowego zawiera klasy otoki, aby klienci zarządzane i niezarządzane, wydaje się, że wywoływania obiektów w ich środowisku odpowiednich. Zawsze, gdy klient zarządzany wywołuje metodę dla obiekt COM, tworzy środowisko uruchomieniowe [wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md) (otoki RCW). RCWs abstrakcyjnej różnice między mechanizmów odwołania zarządzane i niezarządzane, między innymi. Środowisko uruchomieniowe tworzy także [wywoływana otoka COM](com-callable-wrapper.md) (CCW), aby odwrócić procesu włączania klientowi COM bezproblemowo wywołać metody dla obiektu .NET. Jak pokazano na poniższej ilustracji, perspektywy kod wywołujący Określa, która klasa otoki tworzy środowiska uruchomieniowego.  
  
 ![Przegląd otoki COM](media/bidirectional.gif "dwukierunkowych")  
Przegląd otoki COM  
  
 W większości przypadków standardowe otoki RCW lub CCW generowane przez środowisko uruchomieniowe zawiera odpowiednie marshaling dla wywołania, które przekraczają granicę między COM i .NET Framework. Za pomocą atrybutów niestandardowych, można opcjonalnie dostosować sposób środowiska uruchomieniowego reprezentuje kod zarządzane i niezarządzane.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie COM zaawansowane](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))  
 [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)  
 [Wywoływana otoka COM](com-callable-wrapper.md)  
 [Dostosowywanie standardowych otoki](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))  
 [Porady: dostosowywanie wywoływane otoki środowiska uruchomieniowego](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))
