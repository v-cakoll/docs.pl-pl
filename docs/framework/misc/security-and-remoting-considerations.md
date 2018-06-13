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
ms.openlocfilehash: db4a5ee5673ef96c9fb7f39798ab32dd8c910f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398173"
---
# <a name="security-and-remoting-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych i zdalnego dostępu
Usługi zdalne umożliwia konfigurowanie przezroczysty wywoływania między domenami aplikacji, procesy lub komputery. Jednak przeszukiwania stosu zabezpieczeń dostępu kodu nie może przekraczać granice procesu lub maszyny (dotyczy ona między domenami aplikacji tego samego procesu).  
  
 Wszystkie klasy, która może być zastosowana zdalnie (pochodną <xref:System.MarshalByRefObject> klasy) musi przyjąć odpowiedzialność za zabezpieczeń. Albo używanego tylko w środowiskach zamknięte, gdzie jest niejawnie zaufany kod wywołujący lub wywołań zdalnych należy tak zaprojektować, aby nie nakładają chronionych kodu poza wpisu, który może służyć złośliwy kod.  
  
 Ogólnie rzecz biorąc, można powinien nigdy nie ujawnia metody, właściwości lub zdarzeń, które są chronione przez deklaratywne [LinkDemand](../../../docs/framework/misc/link-demands.md) i <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> kontroli zabezpieczeń. Z usług zdalnych kontrole nie są wymuszane. Kontrole zabezpieczeń inne, takie jak <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md)i tak dalej działać między domenami aplikacji w ramach procesu, ale nie działają w scenariuszach międzyprocesowa lub między komputerami.  
  
## <a name="protected-objects"></a>Chronionych obiektów  
 Niektóre obiekty przechowywania stanu zabezpieczeń w sobie. Te obiekty nie powinny być przekazywane do niezaufanych kod, który może uzyskać autoryzacji zabezpieczeń poza własnych uprawnień.  
  
 Przykładem jest utworzenie <xref:System.IO.FileStream> obiektu. <xref:System.Security.Permissions.FileIOPermission> Jest wymagany w czasie tworzenia i, jeśli próba powiedzie się, jest zwracany obiekt pliku. Jednak jeśli to odwołanie do obiektu jest przekazywane do kodu bez uprawnienia do pliku, obiekt będzie do odczytu i zapisu do tego określonego pliku.  
  
 Najprostsza narzędziem do takiego obiektu jest taka sama żądania **FileIOPermission** dowolnego kodu, który próbuje uzyskać odwołania do obiektu za pomocą elementu publicznego interfejsu API.  
  
## <a name="application-domain-crossing-issues"></a>Problemy przecięcia domeny aplikacji  
 Aby wyizolować kodu w zarządzanych środowiskach hostingu, jest często stosowanym rozwiązaniem generowanie wielu domen aplikacji podrzędnych z zasad jawnych zmniejszenie poziomy uprawnień dla różnych zestawów. Jednak zasady dla tych zestawów pozostaje bez zmian w domyślnej domeny aplikacji. Jeśli jeden z domen podrzędnych aplikacji można wymusić domyślnej domeny aplikacji do załadowania zestawu, izolacji kodu powoduje utratę i typów w zestawie wymuszanie załadować będzie można uruchomić kod na wyższym poziomie zaufania.  
  
 Domeny aplikacji można wymusić innej domeny aplikacji w celu załadowania zestawu i uruchomienia kodu zawartych w nim wywołując serwera proxy do obiektu hostowana w innej domenie aplikacji. Uzyskanie proxy między domenami aplikacji, musisz przeprowadzić dystrybucję domeny aplikacji obiektu hosting jeden przez wywołanie metody wartość parametr lub zwracane. Lub, jeśli domena aplikacji został właśnie stworzony, twórca ma serwer proxy <xref:System.AppDomain> obiektu domyślnie. W związku z tym, aby uniknąć dzielenia izolacji kodu, domeny aplikacji na wyższym poziomie zaufania powinien rozpowszechniaj odwołania do obiektów przekazywane przez odwołanie (wystąpienia klas pochodnych <xref:System.MarshalByRefObject>) w swojej domenie do domen aplikacji z małą poziomy zaufania.  
  
 Zazwyczaj domyślnej domeny aplikacji tworzy obiekt podrzędny domeny aplikacji obiektu kontroli w każdej z nich. Obiekt formantu zarządza nowej domeny aplikacji i czasami przyjmuje zamówień z domyślnej domeny aplikacji, ale go nie może faktycznie skontaktuj się z domeny bezpośrednio. Czasami domyślnej domeny aplikacji wywołuje jego agent proxy do obiektu formantu. Jednak może być przypadki, w których jest niezbędna dla obiekt formantu do wywołania zwrotnego domyślnej domeny aplikacji. W takich przypadkach domyślnej domeny aplikacji przekazuje obiekt marshal-by-reference wywołania zwrotnego do konstruktora obiektu formantu. Jest odpowiedzialny za obiektu formantu, aby chronić ten serwer proxy. Jeżeli obiekt formantu umieścić serwer proxy na publicznym statycznym polem publicznej klasy lub w przeciwnym razie publicznie narazić serwer proxy, spowoduje to otwarcie niebezpiecznych mechanizm inny kod do wywołania zwrotnego do domyślnej domeny aplikacji. Z tego powodu obiektach kontroli są zawsze niejawnie zaufanych poufne serwera proxy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
