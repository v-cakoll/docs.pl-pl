---
title: "Porady: ładowanie i zwalnianie zestawów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Porady: ładowanie i zwalnianie zestawów (C#)
Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe ładowanie określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces. Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadować dopóki wszystkie domeny aplikacji, które zawierałoby proces są usuwane z pamięci.  
  
 Aby zwolnić niektóre zestawy, a innych nie, należy rozważyć tworzenia nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwalnianie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Aby załadować zestawu do domeny aplikacji  
  
1.  Użyj załadować jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Aby zwolnić domeny aplikacji  
  
1.  Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces. Użyj `Unload` metody z <xref:System.AppDomain> można zwolnić domeny aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Porady: ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
