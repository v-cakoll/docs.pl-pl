---
title: Obiekty główne i obiekty tożsamości
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfc9a08377a281f7325b120a873fc9b27b8ad856
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="principal-and-identity-objects"></a>Obiekty główne i obiekty tożsamości
Zarządzany kod umożliwia odnalezienie tożsamość lub roli podmiot zabezpieczeń za pomocą <xref:System.Security.Principal.IPrincipal> obiekt, który zawiera odwołanie do <xref:System.Security.Principal.IIdentity> obiektu. Może być przydatne do porównania obiektów tożsamości i podstawowe do znanego pojęć, podobnie jak konta użytkowników i grup. W większości środowisk sieci kont użytkowników reprezentują osób lub programy, podczas gdy konta grupy reprezentują niektórych kategorii użytkowników i praw, które posiadają. Podobnie .NET Framework tożsamości reprezentować użytkowników, gdy reprezentują ról członkostwa i kontekstów zabezpieczeń. W programie .NET Framework obiekt główny hermetyzuje roli i obiektu tożsamości. Aplikacji programu .NET framework przyznać uprawnienia do podmiotu zabezpieczeń na podstawie jego tożsamość lub częściej, członkostwo w roli.  
  
## <a name="identity-objects"></a>Obiekty tożsamości  
 Obiekt identity hermetyzuje informacje dotyczące użytkownika lub jednostka weryfikowana. Na najbardziej podstawowym poziomie obiekty tożsamości zawierają nazwę i typ uwierzytelniania. Nazwa może być nazwa użytkownika lub nazwa konta systemu Windows, typ uwierzytelniania mogą być protokół obsługiwanych logowania, takie jak Kerberos V5 lub niestandardowej wartości. .NET Framework definiuje <xref:System.Security.Principal.GenericIdentity> obiekt, który może służyć do większości scenariuszy niestandardowych logowania i bardziej wyspecjalizowanych <xref:System.Security.Principal.WindowsIdentity> obiekt, który może być używana podczas ma być aplikację do uwierzytelniania systemu Windows. Ponadto można definiować własne klasy tożsamości, który hermetyzuje informacje użytkownika niestandardowego.  
  
 <xref:System.Security.Principal.IIdentity> Interfejs definiuje właściwości nazwę i typ uwierzytelniania, takie jak Kerberos V5 lub NTLM. Wszystkie **tożsamości** implementacji klasy **tożsamości** interfejsu. Nie ma żadnej wymagane zależności między **tożsamości** obiektu i procesów systemu Windows NT tokenu, pod którym wątek jest aktualnie wykonywany. Jednak jeśli **tożsamości** obiekt jest **WindowsIdentity** obiekt przyjęto, że tożsamość reprezentują tokenu zabezpieczeń systemu Windows NT.  
  
## <a name="principal-objects"></a>Obiekty Principal  
 Obiekt główny reprezentuje kontekstu zabezpieczeń, w którym wykonywany jest kod. Aplikacje, które implementują zabezpieczeń opartych na rolach prawa w zależności od roli skojarzone z obiektem podmiotu zabezpieczeń. Podobnie jak obiekty tożsamości, .NET Framework zapewnia <xref:System.Security.Principal.GenericPrincipal> obiektu i <xref:System.Security.Principal.WindowsPrincipal> obiektu. Istnieje również możliwość definiowania własnych niestandardowych klas podmiotu zabezpieczeń.  
  
 <xref:System.Security.Principal.IPrincipal> Interfejs definiuje właściwość do uzyskiwania dostępu do skojarzonego **tożsamości** obiektu, a także metoda ustalania, czy użytkownik jest identyfikowany przez **główna** obiektu jest elementem członkowskim danej roli. Wszystkie **główna** implementacji klasy **IPrincipal** interfejsu oraz wszelkie dodatkowe właściwości i metody, które są niezbędne. Na przykład udostępnia środowisko uruchomieniowe języka wspólnego **WindowsPrincipal** klasy, która implementuje funkcje dodatkowe mapowania członkostwa w grupie systemu Windows NT lub Windows 2000 do ról.  
  
 A **główna** obiektów jest powiązany z kontekstu wywołania (<xref:System.Runtime.Remoting.Messaging.CallContext>) obiektu w obrębie domeny aplikacji (<xref:System.AppDomain>). Domyślny kontekst wywołania zawsze jest tworzony dla każdego nowego **elementu AppDomain**, dzięki czemu jest zawsze dostępne zaakceptować Kontekst wywołania **główna** obiektu. Po utworzeniu nowego wątku **parametr CallContext** obiektu tworzona jest również wątku. **Główna** odwołania do obiektu do jest kopiowana z wątku tworzenia nowego wątku **parametr CallContext**. Jeśli środowisko uruchomieniowe nie może określić, które **główna** obiekt należy do twórca wątku, wynika z domyślnych zasad dla **główna** i **tożsamości** obiektu Tworzenie.  
  
 Zasady właściwe dla domeny można skonfigurować aplikacji definiuje reguł dotyczących decydowania, jaki typ **główna** obiektu do skojarzenia z nowej domeny aplikacji. W przypadku, gdy zasady zabezpieczeń można utworzyć środowisko uruchomieniowe **główna** i **tożsamości** obiektów, które odzwierciedlać token systemu operacyjnego skojarzonego z bieżącego wątku do wykonania. Domyślnie używa środowiska wykonawczego **główna** i **tożsamości** obiektów, które reprezentują nieuwierzytelnionym użytkownikom. Środowisko uruchomieniowe nie tworzy domyślne **główna** i **tożsamości** obiektów dopóki kod próbuje uzyskać do nich dostęp.  
  
 Zaufany kod, który tworzy domenę aplikacji można ustawić zasady domeny aplikacji, które kontrolują konstrukcji domyślnych **główna** i **tożsamości** obiektów. Te zasady właściwe dla domeny aplikacji ma zastosowanie do wszystkich wątków w tej domenie aplikacji. Niezarządzane, zaufanego hosta z założenia ma możliwość określenia tych zasad, ale musi być zarządzany kod ustawiający te zasady <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> do kontrolowania zasad domeny.  
  
 Podczas przekazywania **główna** obiektów między domenami aplikacji, ale w tym samym procesie (i w związku z tym na tym samym komputerze), w zdalnej infrastrukturze kopiuje odwołanie do **główna** obiekt skojarzony z kontekstem wywołującego kontekst wywołującej.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie obiektu WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
 [Instrukcje: tworzenie obiektów GenericPrincipal i GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
 [Zastępowanie obiektu podmiotu zabezpieczeń](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Personifikacja i przywracanie](../../../docs/standard/security/impersonating-and-reverting.md)  
 [Zabezpieczenia oparte na rolach](../../../docs/standard/security/role-based-security.md)  
 [Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)
