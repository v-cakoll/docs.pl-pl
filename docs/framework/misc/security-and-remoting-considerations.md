---
title: Zagadnienia dotyczące zabezpieczeń internetowych i zdalnego dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
ms.openlocfilehash: 7a56c9894da88382f40dcd475e89776a83a59322
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215779"
---
# <a name="security-and-remoting-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych i zdalnego dostępu
Komunikacja zdalna umożliwia skonfigurowanie przezroczystego wywoływania między domenami aplikacji, procesami lub komputerami. Jednak przechodzenie przez stos zabezpieczeń dostępu kodu nie może przekroczyć procesu ani granic maszyn (stosuje się między domenami aplikacji tego samego procesu).  
  
 Każda klasa, która jest zdalna (pochodząca z klasy <xref:System.MarshalByRefObject>) musi podejmować odpowiedzialność za zabezpieczenia. Kod powinien być używany tylko w środowiskach zamkniętych, w których kod wywołujący może być niejawnie zaufany lub wywołania komunikacji zdalnej powinny być zaprojektowane tak, aby nie podlegać chronionemu kodowi, który mógłby być użyty złośliwie.  
  
 Ogólnie rzecz biorąc nie należy ujawniać metod, właściwości ani zdarzeń chronionych przez deklaracyjne [LinkDemand](link-demands.md) i <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> sprawdzenia zabezpieczeń. W przypadku komunikacji zdalnej te sprawdzenia nie są wymuszane. Inne sprawdzenia zabezpieczeń, takie jak <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](using-the-assert-method.md)i tak dalej, działają między domenami aplikacji w ramach procesu, ale nie działają w scenariuszach obejmujących wiele procesów lub międzymaszynowo.  
  
## <a name="protected-objects"></a>Chronione obiekty  
 Niektóre obiekty przechowują stan zabezpieczeń we własnym zakresie. Tych obiektów nie należy przekazywać do niezaufanego kodu, który następnie uzyskuje autoryzację zabezpieczeń poza jej własnymi uprawnieniami.  
  
 Przykładem jest tworzenie obiektu <xref:System.IO.FileStream>. <xref:System.Security.Permissions.FileIOPermission> jest zapotrzebowanie w momencie tworzenia i, jeśli zakończy się pomyślnie, zostanie zwrócony obiekt pliku. Jeśli jednak odwołanie do obiektu zostanie przesłane do kodu bez uprawnień do pliku, obiekt będzie mógł odczytywać i zapisywać dane w tym pliku.  
  
 Najprostszą obroną takiego obiektu jest zażądanie tego samego **FileIOPermission** dowolnego kodu, który poszukuje odwołania do obiektu za pomocą publicznego elementu interfejsu API.  
  
## <a name="application-domain-crossing-issues"></a>Problemy z przekroczeniem domeny aplikacji  
 Aby izolować kod w zarządzanych środowiskach hostingu, często generowane są wiele podrzędnych domen aplikacji z jawnymi zasadami zmniejszającymi poziomy uprawnień dla różnych zestawów. Jednak zasady dla tych zestawów pozostaną niezmienione w domyślnej domenie aplikacji. Jeśli jedna z domen aplikacji podrzędnych może wymusić załadowanie zestawu przez domyślną domenę aplikacji, efekt izolacji kodu zostanie utracony, a typy w załadowanym zestawie będzie można uruchamiać kod na wyższym poziomie zaufania.  
  
 Domena aplikacji może zmusić inną domenę aplikacji do załadowania zestawu i uruchomienia kodu zawartego w nim przez wywołanie serwera proxy do obiektu hostowanego w innej domenie aplikacji. Aby uzyskać serwer proxy domeny między aplikacjami, domena aplikacji hostującym obiekt musi być dystrybuowana przez parametr wywołania metody lub wartość zwracaną. Lub, jeśli domena aplikacji została właśnie utworzona, twórca ma domyślnie serwer proxy obiektu <xref:System.AppDomain>. W ten sposób, aby uniknąć przerywania izolacji kodu, domena aplikacji o wyższym poziomie zaufania nie powinna rozpowszechniać odwołań do obiektów zorganizowanych przez odwołanie (wystąpienia klas pochodzących z <xref:System.MarshalByRefObject>) w swojej domenie do domen aplikacji o niższych poziomach zaufania.  
  
 Zwykle domyślna domena aplikacji tworzy podrzędne domeny aplikacji z obiektem kontrolnym w każdym z nich. Obiekt Control zarządza nową domeną aplikacji i okresowo przyjmuje zamówienia z domyślnej domeny aplikacji, ale nie może fizycznie skontaktować się bezpośrednio z domeną. Czasami domyślna domena aplikacji wywołuje swój serwer proxy do obiektu Control. Mogą jednak wystąpić sytuacje, w których obiekt sterowania może wywoływać z powrotem do domyślnej domeny aplikacji. W takich przypadkach domyślna domena aplikacji przekazuje obiekt wywołania zwrotnego marshal-by-reference do konstruktora obiektu Control. Jest odpowiedzialny za obiekt sterowania do ochrony tego serwera proxy. Jeśli obiekt sterowania miał umieścić serwer proxy w publicznym polu statycznym klasy publicznej lub w inny sposób ujawnia serwer proxy, spowoduje to otwarcie niebezpiecznego mechanizmu dla innego kodu w celu wywołania z powrotem do domyślnej domeny aplikacji. Z tego powodu obiekty sterujące są zawsze niejawnie zaufane, aby zachować prywatny serwer proxy.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
