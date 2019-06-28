---
title: Autoryzacja oparta na oświadczeniach przy użyciu programu WIF
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: 9d20f8fbce916a038fc8224492a4077e1978ed8c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422370"
---
# <a name="claims-based-authorization-using-wif"></a>Autoryzacja oparta na oświadczeniach przy użyciu programu WIF
W aplikacji jednostki uzależnionej autoryzacja określa, do jakich zasobów może uzyskać dostęp uwierzytelniona tożsamość i jakie operacje może wykonywać w odniesieniu do tych zasobów. Niewłaściwa lub słaba autoryzacja może doprowadzić do ujawnienia informacji i nieuprawnionej modyfikacji danych. W tym temacie opisano dostępne sposoby zaimplementowania autoryzacji dla aplikacji i usług internetowych programu ASP.NET obsługujących oświadczenia, za pomocą programu Windows Identity Foundation (WIF) i usługi tokenu zabezpieczającego (STS), na przykład usługi kontroli dostępu (ACS) systemu Microsoft Azure.  
  
## <a name="overview"></a>Omówienie  
 Program .NET Framework od swojej pierwszej wersji oferuje elastyczny mechanizm implementowania autoryzacji. Ten mechanizm opiera się na dwóch prostych interfejsach —**IPrincipal** i **IIdentity**. Konkretne implementacje **IIdentity** reprezentują uwierzytelnionego użytkownika. Na przykład **WindowsIdentity** implementacji reprezentuje użytkownika, który jest uwierzytelniany przez usługę Active Directory i **genericidentity —** reprezentuje użytkownika, którego tożsamość jest weryfikowana przez niestandardowy Proces uwierzytelniania. Konkretne implementacje **IPrincipal** pomagają sprawdzać uprawnienia przy użyciu ról w zależności od magazynu ról. Na przykład **WindowsPrincipal** sprawdza **WindowsIdentity** członkostwa w grupach usługi Active Directory. Ten test jest przeprowadzany przez wywołanie metody **IsInRole** metody **IPrincipal** interfejsu. Sprawdzanie praw dostępu na podstawie ról nazywa się kontrolą dostępu opartą na rolach (Role-Based Access Control, RBAC). Aby uzyskać więcej informacji, zobacz [kontroli dostępu opartej na rolach](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).  Oświadczeń można używać do przenoszenia informacji o rolach w celu obsługi dobrze znanych mechanizmów autoryzacji opartej na rolach.  
  
 Oświadczeń można również używać, aby umożliwić podejmowanie bardziej skomplikowanych decyzji dotyczących autoryzacji, poza rolami. Oświadczenia mogą być oparte na praktycznie dowolnej informacji o użytkowniku — wiek, kod pocztowy, rozmiar buta itp. Mechanizm kontroli dostępu, który jest oparty na dowolnych oświadczeniach nazywa się autoryzacją opartą na oświadczeniach. Aby uzyskać więcej informacji, zobacz [autoryzacji opartej na oświadczeniach](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Kontrola dostępu oparta na rolach  
 RBAC to podejście do autoryzacji, w którym aplikacja zarządza uprawnieniami użytkowników i wymusza je na podstawie ról użytkowników. Jeśli użytkownik pełni rolę, która jest wymagana do wykonywania pewnej czynności, dostęp jest udzielany; w przeciwnym wypadku następuje odmowa dostępu.  
  
### <a name="iprincipalisinrole-method"></a>Metoda IPrincipal.IsInRole  
 Aby zaimplementować podejście RBAC w aplikacjach obsługujących oświadczenia, należy użyć **IsInRole()** method in Class metoda **IPrincipal** interfejsu, tak samo, jak w innych — aplikacji obsługujących oświadczenia. Istnieje kilka sposobów użycia **IsInRole()** metody:  
  
- Jawne wywołanie **IPrincipal.IsInRole("Administrator")** . W tym podejściu wynik jest wartością logiczną. Należy go używać w instrukcjach warunkowych. Można go użyć w dowolny sposób i w dowolnym miejscu w kodzie.  
  
- Za pomocą żądania zabezpieczeń **PrincipalPermission.Demand()** . W tym podejściu wynik jest wyjątkiem w przypadku, gdy wymóg nie jest spełniony. Powinno ono pasować do stosowanej strategii obsługi wyjątków. Zgłaszanie wyjątków jest znacznie bardziej kosztowne z punktu widzenia wydajności w porównaniu do zwracania atrybut typu wartość logiczna. Można go użyć w dowolnym miejscu w kodzie.  
  
- Użycie atrybutów deklaratywnych **[PrincipalPermission (SecurityAction.Demand, Role = "Administrator")]** . To podejście jest nazywane deklaratywnym, ponieważ jest używane do dekorowania metod. Nie można go używać w blokach kodu wewnątrz implementacji metody. Wynik jest wyjątkiem w przypadku, gdy wymóg nie jest spełniony. Należy upewnić się, że to podejście pasuje do stosowanej strategii obsługi wyjątków.  
  
- Za pomocą Autoryzacja adresów URL, za pomocą  **\<autoryzacji >** sekcji **web.config**. To podejście jest odpowiednie w przypadku zarządzania autoryzacją na poziomie adresu URL. Jest to najbardziej zgrubny poziom spośród dotychczas wymienionych. Zaletą tego podejścia jest to, że zmiany są dokonywane w pliku konfiguracji, co oznacza, że nie trzeba kompilować kodu w celu skorzystania ze zmiany.  
  
### <a name="expressing-roles-as-claims"></a>Wyrażanie ról jako oświadczeń  
 Gdy **IsInRole()** metoda jest wywoływana, jest sprawdzenie, czy bieżący użytkownik ma tę rolę. W aplikacjach obsługujących oświadczenia rola jest wyrażana przez typ oświadczenia roli, który powinien być dostępny w tokenie. Typ oświadczenia roli jest wyrażany za pomocą następującego identyfikatora URI:  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 Istnieje kilka sposobów wzbogacenia tokenu o typ oświadczenia roli:  
  
- **Podczas wystawiania tokenu**. Gdy użytkownik jest uwierzytelniany, oświadczenie roli mogą być wystawiane przez usługę STS dostawcy tożsamości lub dostawcy federacyjnego takich jak Windows Azure Access Control Service (ACS).  
  
- **Przekształcenie dowolnych oświadczeń w oświadczenia typu roli za pomocą ClaimsAuthenticationManager**. ClaimsAuthenticationManager jest składnikiem, który wchodzi w skład programu WIF. Pozwala na przechwytywanie żądań, gdy uruchamiają one aplikację, sprawdzanie tokenów i przekształcanie ich przez dodawanie, zmienianie lub usuwanie oświadczeń. Aby uzyskać więcej informacji o sposobie używania składnika ClaimsAuthenticationManager do przekształcania oświadczeń, zobacz [How to: Implementowanie roli na podstawie kontroli dostępu (RBAC) w aplikacji ASP.NET pamiętać oświadczenia, za pomocą programu WIF i usługi ACS](https://go.microsoft.com/fwlink/?LinkID=247445).  
  
- **Zmapowanie dowolnych oświadczeń na typ roli przy użyciu sekcji konfiguracji samlSecurityTokenRequirement**— podejście deklaratywne, w którym przekształcenie oświadczeń jest wykonywane przy użyciu tylko konfiguracji i bez kodowania jest wymagana.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autoryzacja oparta na oświadczeniach  
 Autoryzacja oparta na oświadczeniach to podejście, w którym decyzja o udzieleniu lub odmowie dostępu opiera się na dowolnej logice korzystającej z danych dostępnych w oświadczeniach. Należy przypomnieć, że w przypadku podejścia RBAC jedynym używanym oświadczeniem jest oświadczenie typu roli. Oświadczenie to jest używane do sprawdzenia, czy użytkownik należy do określonej roli, czy nie. Następujące kroki ilustrują proces podejmowania decyzji dotyczących autoryzacji przy użyciu podejścia opartego na oświadczeniach:  
  
1. Aplikacja odbiera żądanie, które wymaga, aby użytkownik został uwierzytelniony.  
  
2. Program WIF przekierowuje użytkownika do jego dostawcy tożsamości, po jego uwierzytelnianiu tworzone jest żądanie aplikacji ze skojarzonym z nim tokenem zabezpieczającym, który reprezentuje użytkownika, zawierającym oświadczenia dotyczące użytkownika. Program WIF kojarzy te oświadczenia z podmiotem zabezpieczeń, który reprezentuje użytkownika.  
  
3. Aplikacja przekazuje oświadczenia do mechanizmu logiki podejmowania decyzji. Może to być kod wewnątrzpamięciowy, wywołanie usługi sieci Web, zapytanie skierowane do bazy danych, zaawansowany aparat reguł lub użycie składnika ClaimsAuthorizationManager.  
  
4. Mechanizm podejmowania decyzji oblicza wynik na podstawie oświadczeń.  
  
5. Dostęp jest udzielany, jeśli wynikiem jest „prawda”; jeśli wynikiem jest „fałsz”, następuje odmowa dostępu. Na przykład reguła może wymagać, aby użytkownik był w wieku 21 lub starszy i mieszkał w stanie Waszyngton.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> przydaje się do eksternalizacji logiki podejmowania decyzji dla autoryzacji opartej na oświadczeniach w aplikacjach. ClaimsAuthorizationManager jest składnikiem programu WIF, który wchodzi w skład platformy .NET 4.5. Składnik ClaimsAuthorizationManager pozwala na przechwytywanie żądań przychodzących i zaimplementowanie dowolnej logiki wybranej do podejmowania decyzji dotyczących autoryzacji na podstawie oświadczeń przychodzących. Staje się to ważne, jeśli logika autoryzacji musi zostać zmieniona. W takim przypadku użycie składnika ClaimsAuthorizationManager nie wpływa na integralność aplikacji, zmniejszając w ten sposób prawdopodobieństwo wystąpienia błędu aplikacji w wyniku zmiany. Aby dowiedzieć się więcej o sposobie używania składnika ClaimsAuthorizationManager do implementacji kontroli dostępu opartej na oświadczeniach, zobacz [How to: Implementowanie oświadczeń autoryzacji w aplikacji ASP.NET pamiętać oświadczenia, za pomocą programu WIF i usługi ACS](https://go.microsoft.com/fwlink/?LinkID=247446).
