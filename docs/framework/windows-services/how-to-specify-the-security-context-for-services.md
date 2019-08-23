---
title: 'Instrukcje: Określanie kontekstu zabezpieczeń dla usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 88dc9c40a2b8ff0ac9bba26c991ba2a4ac2dcb43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952437"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Instrukcje: Określanie kontekstu zabezpieczeń dla usług
Domyślnie usługi są uruchamiane w innym kontekście zabezpieczeń niż zalogowany użytkownik. Usługi są uruchamiane w kontekście domyślnego konta systemowego o nazwie `LocalSystem`, które daje im różne uprawnienia dostępu do zasobów systemowych niż użytkownik. Możesz zmienić to zachowanie, aby określić inne konto użytkownika, w ramach którego ma zostać uruchomiona usługa.  
  
 Kontekst zabezpieczeń jest ustawiany przez manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwością procesu, w którym działa usługa. Ta właściwość umożliwia ustawienie jednego z czterech typów kont:  
  
- `User`, co powoduje, że system monituje o podanie prawidłowej nazwy użytkownika i hasła podczas instalacji usługi i jest uruchamiany w kontekście konta określonego przez pojedynczego użytkownika w sieci;  
  
- `LocalService`, który działa w kontekście konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i przedstawia anonimowe poświadczenia na dowolnym serwerze zdalnym;  
  
- `LocalSystem`, który działa w kontekście konta, które zapewnia szerokie uprawnienia lokalne, i przedstawia poświadczenia komputera na dowolnym serwerze zdalnym;  
  
- `NetworkService`, który działa w kontekście konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i przedstawia poświadczenia komputera na dowolnym serwerze zdalnym.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> Wyliczenie.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Aby określić kontekst zabezpieczeń dla usługi  
  
1. Po utworzeniu usługi należy dodać do niej niezbędne Instalatory. Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)usługi.  
  
2. W projektancie uzyskaj dostęp `ProjectInstaller` do klasy i kliknij Instalatora procesów usługi dla usługi, z którą pracujesz.  
  
    > [!NOTE]
    > Dla każdej aplikacji usługi w `ProjectInstaller` klasie istnieją co najmniej dwa składniki instalacyjne — jedną, która instaluje procesy dla wszystkich usług w projekcie, oraz jeden Instalator dla każdej usługi zawierającej daną aplikację. W tym przypadku należy wybrać opcję <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3. W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpowiednią wartość.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
