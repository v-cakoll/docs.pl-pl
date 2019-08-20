---
title: 'Instrukcje: Ładowanie i zwalnianie zestawówC#()'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 3f3c244a74e029eeaead77f561cd4c1adfca519a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595838"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Instrukcje: Ładowanie i zwalnianie zestawówC#()
Zestawy, do których odwołuje się program, zostaną automatycznie załadowane w czasie kompilacji, ale możliwe jest również załadowanie określonych zestawów do domeny bieżącej aplikacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikacji.  
  
 Nie ma możliwości zwolnienia pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Nawet jeśli zestaw wykracza poza zakres, rzeczywisty plik zestawu pozostanie załadowany do momentu, gdy wszystkie domeny aplikacji, które go zawierają, zostaną zwolnione.  
  
 Jeśli chcesz usunąć niektóre zestawy, ale nie inne, rozważ utworzenie nowej domeny aplikacji, wykonanie kodu w tej domenie, a następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnij domenę](../../../../framework/app-domains/how-to-unload-an-application-domain.md)aplikacji.  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Aby załadować zestaw do domeny aplikacji  
  
1. Użyj jednej z kilku metod obciążenia zawartych w klasach <xref:System.AppDomain> i. <xref:System.Reflection> Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikacji.  
  
### <a name="to-unload-an-application-domain"></a>Aby zwolnić domenę aplikacji  
  
1. Nie ma możliwości zwolnienia pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Użyj metody z <xref:System.AppDomain> , aby zwolnić domeny aplikacji. `Unload` Aby uzyskać więcej informacji, zobacz [jak: Zwolnij domenę](../../../../framework/app-domains/how-to-unload-an-application-domain.md)aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
