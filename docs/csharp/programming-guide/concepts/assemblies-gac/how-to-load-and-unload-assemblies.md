---
title: 'Instrukcje: Ładowanie i zwalnianie zestawów (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 52f7173efe497ab286c607db681f256983adc077
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342046"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Instrukcje: Ładowanie i zwalnianie zestawów (C#)
Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe do załadowania określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Nie ma możliwości wyładować poszczególnych zestawów bez rozładowywania wszystkich domen aplikacji, które go zawierają. Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadowane, dopóki wszystkie domeny aplikacji, które go zawierają są usuwane z pamięci.  
  
 Aby zwolnić niektóre zestawy, a nie innych, należy rozważyć tworzenie nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Ładowanie zestawów do domeny aplikacji  
  
1. Użyj obciążenia jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Aby zwolnienie domeny aplikacji  
  
1. Nie ma możliwości wyładować poszczególnych zestawów bez rozładowywania wszystkich domen aplikacji, które go zawierają. Użyj `Unload` metody z <xref:System.AppDomain> wyładować domen aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
