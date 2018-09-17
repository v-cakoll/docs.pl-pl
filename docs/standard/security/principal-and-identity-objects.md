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
ms.openlocfilehash: b8c7616a3187cd5fa28f231dffd15b0bfeea4b7f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45696039"
---
# <a name="principal-and-identity-objects"></a>Obiekty główne i obiekty tożsamości
Kod zarządzany może odnaleźć tożsamości lub roli jednostki za pośrednictwem <xref:System.Security.Principal.IPrincipal> obiekt, który zawiera odwołanie do <xref:System.Security.Principal.IIdentity> obiektu. Może być przydatne do porównania obiektów tożsamości i jednostki do znanych pojęć, takich jak konta użytkowników i grup. W większości środowisk sieciowych konta użytkowników reprezentują osób lub programów, podczas gdy konta grupy reprezentują niektóre kategorie użytkownicy i prawa, które posiadają. Podobnie obiekty tożsamości .NET Framework reprezentuje użytkowników, gdy role reprezentowania członkostwa i konteksty zabezpieczeń. W .NET Framework obiekt główny hermetyzuje roli i obiektu tożsamości. Aplikacje programu .NET framework udziela praw do jednostki, na podstawie jego tożsamości lub częściej, członkostwo w roli.  
  
## <a name="identity-objects"></a>Obiekty tożsamości  
 Tożsamość hermetyzuje informacje dotyczące użytkownika lub jednostka weryfikowana. Na najbardziej podstawowym poziomie obiekty tożsamości zawierają nazwę i typ uwierzytelniania. Nazwa może być nazwa użytkownika lub nazwa konta Windows, mogą być typ uwierzytelniania, protokół obsługiwanych logowania, takie jak protokół Kerberos V5 lub niestandardowej wartości. .NET Framework definiuje <xref:System.Security.Principal.GenericIdentity> obiekt, który może służyć do większości scenariuszy logowania niestandardowych i bardziej wyspecjalizowane <xref:System.Security.Principal.WindowsIdentity> obiekt, który można użyć, gdy chcesz, aby aplikacja polegać na uwierzytelnianie Windows. Ponadto można zdefiniować własne klasy tożsamości, który hermetyzuje informacje użytkownika niestandardowego.  
  
 <xref:System.Security.Principal.IIdentity> Interfejs definiuje właściwości do uzyskiwania dostępu do nazwę i typ uwierzytelniania, takich jak Kerberos V5 lub NTLM. Wszystkie **tożsamości** implementacji klasy **IIdentity** interfejsu. Nie ma wymaganych relacji między **tożsamości** obiektów i procesów systemu Windows NT tokenu, pod którym wątek jest w trakcie wykonywania. Jednak jeśli **tożsamości** obiekt jest **WindowsIdentity** obiektu tożsamości założono, że reprezentuje token zabezpieczeń Windows NT.  
  
## <a name="principal-objects"></a>Obiekty nazwę głównej  
 Obiekt podmiotu zabezpieczeń reprezentuje kontekstu zabezpieczeń, w którym jest uruchomiony kod. Aplikacje, które implementują opartej na rolach zabezpieczeń udziela praw, w zależności od roli skojarzony obiekt podmiotu zabezpieczeń. Podobnie jak obiekty tożsamości, program .NET Framework oferuje <xref:System.Security.Principal.GenericPrincipal> obiektu i <xref:System.Security.Principal.WindowsPrincipal> obiektu. Można również definiować własne klasy jednostki niestandardowe.  
  
 <xref:System.Security.Principal.IPrincipal> Interfejs definiuje właściwość do uzyskiwania dostępu do skojarzonego **tożsamości** obiektu, a także metoda określania, czy użytkownik jest identyfikowany przez **jednostki** obiektu jest elementem członkowskim danej roli. Wszystkie **jednostki** implementacji klasy **IPrincipal** interfejsu, jak również wszelkie dodatkowe właściwości i metody, które są niezbędne. Na przykład, środowisko uruchomieniowe języka wspólnego udostępnia **WindowsPrincipal** klasy, która implementuje dodatkowe funkcje do mapowania członkostwa w grupie Windows NT lub Windows 2000 do ról.  
  
 A **jednostki** obiekt jest powiązany do kontekstu wywołania (<xref:System.Runtime.Remoting.Messaging.CallContext>) obiektów w domenie aplikacji (<xref:System.AppDomain>). Domyślny kontekst wywołania zawsze jest tworzony dla każdego nowego **AppDomain**, dzięki czemu jest zawsze dostępne zaakceptować Kontekst wywołania **jednostki** obiektu. Po utworzeniu nowego wątku **CallContext** obiektu również jest tworzony dla wątku. **Jednostki** odwołanie do obiektu do jest kopiowana z wątku tworzącego nowy wątek **CallContext**. Jeśli środowisko wykonawcze nie może ustalić, który **jednostki** obiekt należy do twórcy wątku, jest zgodna z domyślną zasadę dla **jednostki** i **tożsamości** obiektu Tworzenie.  
  
 Zasady specyficznego dla domeny aplikacji można skonfigurować definiuje reguły decydujące o tym, jaki typ **jednostki** obiektu do skojarzenia z nowej domeny aplikacji. W przypadku, gdy zasady zabezpieczeń można utworzyć środowisko uruchomieniowe **jednostki** i **tożsamości** obiekty, które odzwierciedlają token systemu operacyjnego skojarzony z bieżącym wątkiem wykonywania. Domyślnie środowisko uruchomieniowe używa **jednostki** i **tożsamości** obiekty reprezentujące nieuwierzytelnionym użytkownikom. Środowisko wykonawcze nie tworzy domyślne **jednostki** i **tożsamości** obiektów, dopóki kod próbuje uzyskać do nich dostęp.  
  
 Zaufany kod, który tworzy domenę aplikacji można ustawić zasady domeny aplikacji, które kontrolują konstrukcji domyślnych **jednostki** i **tożsamości** obiektów. Ta zasada specyficznego dla domeny aplikacji ma zastosowanie do wszystkich wątków w tej domenie aplikacji. Niezarządzane, zaufanego hosta natury ma zdolność ustawiania tych zasad, ale kodu zarządzanego, który ustawia te zasady muszą mieć <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> do kontrolowania zasad domeny.  
  
 Przy przekazywaniu **jednostki** obiektu w różnych domenach aplikacji, ale w obrębie tego samego procesu (i w związku z tym na tym samym komputerze), infrastruktury usług zdalnych kopiuje odwołanie do **jednostki** obiekt skojarzony z kontekstem wywołującego / / wywoływany kontekst.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie obiektu WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
- [Instrukcje: tworzenie obiektów GenericPrincipal i GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
- [Zastępowanie obiektu podmiotu zabezpieczeń](../../../docs/standard/security/replacing-a-principal-object.md)  
- [Personifikacja i przywracanie](../../../docs/standard/security/impersonating-and-reverting.md)  
- [Zabezpieczenia oparte na rolach](../../../docs/standard/security/role-based-security.md)  
- [Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)
