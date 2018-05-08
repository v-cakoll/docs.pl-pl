---
title: 'Porady: określanie kontekstu zabezpieczeń dla usług'
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
manager: douge
ms.openlocfilehash: e3e5ad7dd44dcaf1593ac80bbe6d0a367964e4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-security-context-for-services"></a>Porady: określanie kontekstu zabezpieczeń dla usług
Domyślnie usługi uruchamiane w kontekście zabezpieczeń inną niż zalogowanego użytkownika. Usługi uruchamiane w kontekście domyślnego konta systemu o nazwie `LocalSystem`, która umożliwi im różne przywileje dostępu do zasobów systemowych od użytkownika. Można zmienić to zachowanie, aby określić inne konto użytkownika usługi powinny uruchamiania.  
  
 Ustaw kontekst zabezpieczeń przez manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwości dla procesu, w którym jest uruchamiana usługa. Ta właściwość pozwala ustawić jedną z czterech typy kont usługi:  
  
-   `User`, co powoduje, że system z monitem o prawidłowej nazwy użytkownika i hasła, gdy usługa jest zainstalowana i działa w kontekście konta określonego przez pojedynczego użytkownika w sieci, a  
  
-   `LocalService`, które są uruchamiane w kontekście konta działa jako użytkownik bez uprawnień na komputerze lokalnym, przedstawiając poświadczeń anonimowego do dowolnego serwera zdalnego;  
  
-   `LocalSystem`, które są uruchamiane w kontekście konta, które udostępnia szerokie uprawnienia lokalnego, przedstawiając poświadczeń komputera do dowolnego serwera zdalnego;  
  
-   `NetworkService`, które są uruchamiane w kontekście konta działa jako użytkownik bez uprawnień na komputerze lokalnym, przedstawiając poświadczeń komputera do dowolnego serwera zdalnego.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> wyliczenia.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Aby określić kontekstu zabezpieczeń dla usługi  
  
1.  Po utworzeniu usługi, należy dodać wymagane pliki instalacyjne dla niego. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  W Projektancie dostępu `ProjectInstaller` klasy, a następnie kliknij przycisk Instalatora procesu usługi dla usługi pracujesz.  
  
    > [!NOTE]
    >  Dla każdej aplikacji usługi istnieją co najmniej dwa składniki instalacji w `ProjectInstaller` klasy —, który instaluje procesy dla wszystkich usług w projekcie oraz jednego Instalatora dla każdej usługi, ta aplikacja zawiera. W tym wystąpieniu chcesz wybrać <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  W **właściwości** ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpowiednią wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
