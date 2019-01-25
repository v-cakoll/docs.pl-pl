---
title: Zagadnienia dotyczące zabezpieczeń internetowych i zdalnego dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39b7bcec1196a59c47717ec2b5622ca8e0d3cdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591995"
---
# <a name="security-and-remoting-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych i zdalnego dostępu
Wywołaniem funkcji zdalnych pozwala skonfigurować przezroczyste wywoływaniu między domenami aplikacji, procesy lub komputerów. Jednak przeszukiwania stosu zabezpieczeń dostępu kodu nie może przekraczać granice procesu i maszynowo lub (dotyczy ona między domenami aplikacji tego samego procesu).  
  
 Wszystkie klasy, która może być zastosowana zdalnie (pochodną <xref:System.MarshalByRefObject> klasy) musi odpowiadać za zabezpieczenia. Albo kod stosuje się tylko w środowiskach zamknięte, w którym kod wywołujący może być niejawnie zaufanych lub wywołaniem funkcji zdalnych wywołań powinny zostać tak zaprojektowane, tak aby nie podlegają chroniony kod poza wpisem, która mogłaby być używana w sposób złośliwy.  
  
 Ogólnie rzecz biorąc, należy nigdy nie udostępnić metody, właściwości lub zdarzenia, które są chronione przez deklaratywne [LinkDemand](../../../docs/framework/misc/link-demands.md) i <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> sprawdzanie zabezpieczeń. Te sprawdzenia z wywołaniem funkcji zdalnych, nie są wymuszane. Kontrole zabezpieczeń inne, takie jak <xref:System.Security.Permissions.SecurityAction.Demand>, [Asercja](../../../docs/framework/misc/using-the-assert-method.md)i tak dalej działać między domenami aplikacji w ramach procesu, ale nie działają w scenariuszach między procesami lub między komputerami.  
  
## <a name="protected-objects"></a>Chronione obiekty  
 Niektóre obiekty przechowywać stan zabezpieczeń w sobie. Te obiekty nie powinny być przekazywane do niezaufanego kodu, który może uzyskać autoryzacji zabezpieczeń poza własnych uprawnień.  
  
 Przykładem jest utworzenie <xref:System.IO.FileStream> obiektu. <xref:System.Security.Permissions.FileIOPermission> Jest wymagany w czasie tworzenia i, jeśli się powiedzie, zwracany jest obiektu pliku. Jednak jeśli odwołanie do tego obiektu jest przekazywany do kodu bez uprawnienia do pliku, obiekt będzie do odczytu i zapisu do tego określonego pliku.  
  
 Najprostsza podstawowym narzędziem do takiego obiektu jest takie same żądania **FileIOPermission** dowolnego kodu, który próbuje uzyskać odwołanie do obiektu za pomocą elementu publicznego interfejsu API.  
  
## <a name="application-domain-crossing-issues"></a>Problemy występujące w wielu domen aplikacji  
 Aby wyizolować kod w zarządzanych środowiskach hostingu, są często można wygenerować wiele domen aplikacji podrzędnych za pomocą zasad jawnych zmniejszenie poziomy uprawnień dla różnych zestawów. Jednak zasady dla tych zestawów pozostaje bez zmian w domyślnej domeny aplikacji. Jeśli jeden z domen podrzędnych w aplikacji można wymusić domyślnej domeny aplikacji do załadowania zestawu, izolacja kodu powoduje utratę i typów w zestawie wymuszone załadować będą mogli uruchamianie kodu na wyższym poziomie zaufania.  
  
 Domeny aplikacji można wymusić w innej domenie aplikacji, które można załadować zestawu i uruchomić kod, składających się na nie przez wywołanie serwera proxy do obiektu hostowanej w innej domenie aplikacji. Można uzyskać serwera proxy między domenami aplikacji, musisz przeprowadzić dystrybucję domeny aplikacji obiektu hostingu jeden przez metodę wywołania parametrze lub wartości zwracanej. Lub, jeśli domena aplikacji zostało właśnie utworzone, Autor ma serwer proxy, aby <xref:System.AppDomain> obiektu domyślnie. W związku z tym, aby uniknąć dzielenia izolacji kodu, domenę aplikacji z wyższego poziomu zaufania powinna nie dystrybuować odwołania do obiektów przekazywane przez odwołanie (wystąpienia klas pochodnych <xref:System.MarshalByRefObject>) w swojej domenie domen aplikacji z dolnym poziomy zaufania.  
  
 Zazwyczaj domyślnej domeny aplikacji tworzy element podrzędny domeny aplikacji za pomocą obiektu formantu w każdej z nich. Obiekt formantu zarządza nową domenę aplikacji, a od czasu do czasu zajmuje zamówienia z domyślnej domeny aplikacji, ale go nie może faktycznie skontaktuj się z domeny bezpośrednio. Od czasu do czasu domyślnej domeny aplikacji wywołuje jego agent proxy do obiektu formantu. Jednak może być przypadki, w których jest wymagane dla obiektu formantu do wywołania zwrotnego do domyślnej domeny aplikacji. W takich przypadkach domyślnej domeny aplikacji przekazuje obiekt wywołania zwrotnego marshal-by-reference do konstruktora obiektu formantu. Jest odpowiedzialny za obiekt formantu, aby chronić ten serwer proxy. Jeżeli obiekt formantu Umieść serwer proxy na publiczne pole statyczne klasy publicznej lub w przeciwnym razie uwidoczniają publicznie serwera proxy, to czy otwierają niebezpiecznych mechanizm dla innego kodu, wywołanie domyślnej domeny aplikacji. Z tego powodu obiekty kontrolek są zawsze niejawnie zaufany w celu zachowania prywatności serwera proxy.  
  
## <a name="see-also"></a>Zobacz także
- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
