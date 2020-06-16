---
title: Obiekty główne i obiekty tożsamości
description: Przeczytaj informacje o obiektach tożsamości, które reprezentują użytkowników w programie .NET. Zapoznaj się również z obiektami podmiotu zabezpieczeń, które hermetyzują zarówno obiekt tożsamości & rolę.
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
ms.openlocfilehash: 5fd3f1c80f22c1ebe7b2c10653ee137f00321de8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768849"
---
# <a name="principal-and-identity-objects"></a>Obiekty główne i obiekty tożsamości
Kod zarządzany może wykryć tożsamość lub rolę podmiotu zabezpieczeń za pomocą <xref:System.Security.Principal.IPrincipal> obiektu, który zawiera odwołanie do <xref:System.Security.Principal.IIdentity> obiektu. Pomocne może być porównanie tożsamości i obiektów głównych z znanymi pojęciami, takimi jak konta użytkowników i grup. W większości środowisk sieciowych konta użytkowników reprezentują osoby lub programy, natomiast konta grup reprezentują pewne kategorie użytkowników i prawa, które posiada. Podobnie obiekty tożsamości .NET Framework reprezentują użytkowników, natomiast role reprezentują członkostwa i konteksty zabezpieczeń. W .NET Framework obiekt Principal hermetyzuje zarówno obiekt tożsamości, jak i rolę. .NET Framework aplikacje przyznają uprawnienia do podmiotu zabezpieczeń na podstawie jego tożsamości lub, częściej, przynależności do roli.  
  
## <a name="identity-objects"></a>Obiekty tożsamości  
 Obiekt Identity hermetyzuje informacje o zweryfikowanym użytkowniku lub jednostce. Na poziomie podstawowym obiekty tożsamości zawierają nazwę i typ uwierzytelniania. Może to być nazwa użytkownika lub nazwa konta systemu Windows, podczas gdy typem uwierzytelniania może być obsługiwany protokół logowania, taki jak Kerberos V5 lub wartość niestandardowa. .NET Framework definiuje <xref:System.Security.Principal.GenericIdentity> obiekt, którego można użyć w przypadku większości niestandardowych scenariuszy logowania i bardziej wyspecjalizowany <xref:System.Security.Principal.WindowsIdentity> obiekt, którego można użyć, gdy aplikacja ma korzystać z uwierzytelniania systemu Windows. Ponadto możesz zdefiniować własną klasę tożsamości, która hermetyzuje niestandardowe informacje o użytkownikach.  
  
 <xref:System.Security.Principal.IIdentity>Interfejs definiuje właściwości dostępu do nazwy i typu uwierzytelniania, takich jak Kerberos V5 lub NTLM. Wszystkie klasy **tożsamości** implementują interfejs **IIdentity** . Nie istnieje żadna wymagana relacja między obiektem **Identity** i tokenem procesu systemu Windows NT, w ramach którego aktualnie wykonywany jest wątek. Jeśli jednak obiekt **Identity** jest obiektem **WindowsIdentity** , założono, że tożsamość reprezentuje token zabezpieczający systemu Windows NT.  
  
## <a name="principal-objects"></a>Obiekty główne  
 Obiekt Principal reprezentuje kontekst zabezpieczeń, w którym jest uruchomiony kod. Aplikacje implementujące prawa do przyznawania zabezpieczeń oparte na rolach w oparciu o rolę skojarzoną z obiektem Principal. Podobnie jak w przypadku obiektów tożsamości, .NET Framework zapewnia <xref:System.Security.Principal.GenericPrincipal> obiekt i <xref:System.Security.Principal.WindowsPrincipal> obiekt. Można także definiować własne niestandardowe klasy główne.  
  
 <xref:System.Security.Principal.IPrincipal>Interfejs definiuje Właściwość uzyskiwania dostępu do skojarzonego obiektu **tożsamości** , a także metodę określania, czy użytkownik identyfikowany przez obiekt **Principal** jest członkiem danej roli. Wszystkie klasy **Główne** implementują interfejs **IPrincipal** oraz wszelkie dodatkowe właściwości i metody, które są niezbędne. Na przykład środowisko uruchomieniowe języka wspólnego udostępnia klasę **WindowsPrincipal** , która implementuje dodatkowe funkcje mapowania członkostwa grupy systemu Windows NT lub Windows 2000 do ról.  
  
 Obiekt **Principal** jest powiązany z obiektem kontekstu wywołania ( <xref:System.Runtime.Remoting.Messaging.CallContext> ) w domenie aplikacji ( <xref:System.AppDomain> ). Domyślny kontekst wywołania jest zawsze tworzony z każdą nową **domeną aplikacji**, więc zawsze jest dostępny kontekst wywołania do akceptowania obiektu **głównego** . Po utworzeniu nowego wątku tworzony jest również obiekt **CallContext** dla wątku. Odwołanie do obiektu **głównego** jest automatycznie kopiowane z wątku tworzenia do **CallContext**nowego wątku. Jeśli środowisko wykonawcze nie może ustalić, który obiekt **główny** należy do twórcy wątku, następuje po zasadach domyślnych dla tworzenia obiektów **podmiotu zabezpieczeń** i **tożsamości** .  
  
 Konfigurowalne zasady specyficzne dla domeny aplikacji definiują reguły decydujące o typie obiektu **podmiotu zabezpieczeń** , który ma zostać skojarzony z nową domeną aplikacji. W przypadku, gdy zasady zabezpieczeń pozwalają, środowisko uruchomieniowe może utworzyć obiekty **Principal** i **Identity** , które odzwierciedlają token systemu operacyjnego skojarzony z bieżącym wątkiem wykonywania. Domyślnie środowisko uruchomieniowe używa obiektów **Principal** i **Identity** , które reprezentują nieuwierzytelnionych użytkowników. Środowisko uruchomieniowe nie tworzy tych domyślnych obiektów **głównych** i **tożsamości** , dopóki kod nie spróbuje uzyskać do nich dostępu.  
  
 Zaufany kod, który tworzy domenę aplikacji, może ustawić zasady domeny aplikacji kontrolujące konstruowanie domyślnych obiektów **głównych** i **tożsamości** . Te zasady specyficzne dla domeny aplikacji mają zastosowanie do wszystkich wątków wykonywania w tej domenie aplikacji. Niezarządzany, zaufany Host nieodłącznie ma możliwość ustawienia tych zasad, ale kod zarządzany, który ustawia te zasady, musi mieć uprawnienia <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> do kontrolowania zasad domeny.  
  
 Podczas przesyłania obiektu **podmiotu zabezpieczeń** między domenami aplikacji, ale w ramach tego samego procesu (i w związku z tym na tym samym komputerze) infrastruktura zdalna kopiuje odwołanie do obiektu **podmiotu zabezpieczeń** skojarzonego z kontekstem obiektu wywołującego do kontekstu wywoływanego.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie obiektu WindowsPrincipal](how-to-create-a-windowsprincipal-object.md)
- [Porady: tworzenie obiektów GenericPrincipal i GenericIdentity](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Zastępowanie obiektu podmiotu zabezpieczeń](replacing-a-principal-object.md)
- [Personifikacja i przywracanie](impersonating-and-reverting.md)
- [Zabezpieczenia oparte na rolach](role-based-security.md)
- [Główne pojęcia dotyczące zabezpieczeń](key-security-concepts.md)
