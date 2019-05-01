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
ms.openlocfilehash: 68fd5d705cb2f38e00e90c211111ff34d23f3b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913890"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Instrukcje: Określanie kontekstu zabezpieczeń dla usług
Domyślnie usługi uruchamiane w kontekście zabezpieczeń inny niż zalogowany użytkownik. Usługi uruchamiane w kontekście domyślnego konta systemu o nazwie `LocalSystem`, która umożliwi im różne przywileje dostępu do zasobów systemowych, nie użytkownik. Możesz zmienić to zachowanie, aby określić inne konto użytkownika na którym jest uruchamiany z usługą.  
  
 Ustaw kontekst zabezpieczeń, manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwości dla procesu, w którym usługa jest uruchamiana. Ta właściwość umożliwia ustawianie usługi do zestawu obejmującego cztery typy konta:  
  
- `User`, która sprawia, że system wyświetla monit o podanie prawidłowej nazwy użytkownika i hasła, gdy usługa jest zainstalowana i działa w kontekście konta określonego przez pojedynczego użytkownika w sieci.  
  
- `LocalService`, które są uruchamiane w kontekście konta, który działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi;  
  
- `LocalSystem`, które są uruchamiane w kontekście konta, które zapewnia szerokie uprawnienia lokalnego i przedstawia poświadczenia komputera każdemu zdalnemu serwerowi;  
  
- `NetworkService`, które są uruchamiane w kontekście konta, który działa jako użytkownik bez uprawnień na komputerze lokalnym, a poświadczenia komputera każdemu zdalnemu serwerowi przedstawia.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> wyliczenia.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Do określenia kontekstu zabezpieczeń dla usługi  
  
1. Po utworzeniu usługi, dodanie niezbędnych instalatorów dla niego. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2. W Projektancie dostępu `ProjectInstaller` klasy, a następnie kliknij przycisk Instalatora procesu usługi dla usługi, którymi pracujesz.  
  
    > [!NOTE]
    >  Dla każdej aplikacji usługi są co najmniej dwa składniki instalacyjne w `ProjectInstaller` klasy — taki, który instaluje procesów dla wszystkich usług w projekcie i jednego Instalatora dla każdej usługi, które zawiera aplikację. W tym przypadku chcesz wybrać <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3. W **właściwości** oknie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpowiednią wartość.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Tworzenie usług Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
