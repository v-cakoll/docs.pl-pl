---
title: Otoki COM
description: Klienci modelu COM i obiekty .NET współdziałają z użyciem otoki, która umożliwia wywoływanie modelu COM i otokę umożliwiającą wywoływanie Środowisko CLR tworzy otoki automatycznie.
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: f1cf84b8f15de1e3bd19a391767f5573f01ff806
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420516"
---
# <a name="com-wrappers"></a>Otoki COM
COM różni się od modelu obiektów środowiska uruchomieniowego .NET na kilka ważnych sposobów:  
  
- Klienci obiektów COM muszą zarządzać okresem istnienia tych obiektów; środowisko uruchomieniowe języka wspólnego zarządza okresem istnienia obiektów w jego środowisku.  
  
- Klienci obiektów COM wykrywają, czy usługa jest dostępna przez żądanie interfejsu, który zapewnia tę usługę, i przywracający wskaźnik interfejsu, czy nie. Klienci obiektów .NET mogą uzyskać opis funkcji obiektu przy użyciu odbicia.  
  
- Obiekty sieciowe znajdują się w pamięci zarządzanej przez środowisko wykonawcze środowiska uruchomieniowego platformy .NET. Środowisko wykonawcze może przenosić obiekty w pamięci ze względu na wydajność i aktualizować wszystkie odwołania do obiektów, które są przez niego przenoszone. Niezarządzani Klienci, którzy uzyskali wskaźnik do obiektu, zależą od obiektu, aby pozostawał w tej samej lokalizacji. Ci klienci nie mają mechanizmu do zajmowania się obiektem, którego lokalizacja nie jest stała.  
  
 Aby przezwyciężyć te różnice, środowisko uruchomieniowe zapewnia klasy otoki, aby zarówno klienci zarządzani, jak i niezarządzani, uważali, że wywołujeją obiekty w ramach danego środowiska. Za każdym razem, gdy zarządzany klient wywołuje metodę dla obiektu COM, środowisko uruchomieniowe tworzy niewywołującą otokę (otoka [środowiska uruchomieniowego](runtime-callable-wrapper.md) ). RCW abstrakcyjne różnice między zarządzanymi i niezarządzanymi mechanizmami odniesienia, między innymi. Środowisko uruchomieniowe powoduje także utworzenie [otoki](com-callable-wrapper.md) wywołującej com (CCW) w celu odwrócenia procesu, co umożliwia KLIENTowi com bezproblemową wywoływanie metody dla obiektu .NET. Jak widać na poniższej ilustracji, perspektywa kodu wywołującego określa klasę otoki, którą tworzy środowisko uruchomieniowe.  
  
 ![Omówienie otoki COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 W większości przypadków standardowa OTOKa lub CCW wygenerowane przez środowisko uruchomieniowe zapewniają odpowiednie kierowanie dla wywołań, które przecinają granicę między modelem COM a środowiskiem uruchomieniowym platformy .NET. Przy użyciu atrybutów niestandardowych można opcjonalnie dostosować sposób, w jaki środowisko uruchomieniowe reprezentuje kod zarządzany i niezarządzany.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane współdziałanie COM w .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)
- [Wywoływana otoka COM](com-callable-wrapper.md)
- [Dostosowywanie otok standardowych w .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Instrukcje: Dostosowywanie wywoływanych otok środowiska uruchomieniowego w .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))
