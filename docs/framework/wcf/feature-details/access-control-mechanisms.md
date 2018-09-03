---
title: Mechanizmy kontroli dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 1de6731591e524080ac4ae7d5b2ec2a25a27f301
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486665"
---
# <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu
Możesz kontrolować dostęp w kilku sposób za pomocą programu Windows Communication Foundation (WCF). W tym temacie krótko omówiono różne mechanizmy i sugestie, kiedy należy używać każdego; jest ona przeznaczona do ułatwienia wybrania poprawne mechanizm do użycia. Technologie dostępu są wymienione w kolejności złożoności. To najprostszy <xref:System.Security.Permissions.PrincipalPermissionAttribute>; najbardziej złożone jest modelu tożsamości.  
  
 Oprócz tych mechanizmów personifikacji i delegowanie z programem WCF została wyjaśniona w [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest używany do ograniczania dostępu do metody usługi. Jeśli ten atrybut jest stosowany do metody, może służyć do obiektu wywołującego określonych tożsamości lub członkostwo w grupie Windows lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli. Jeśli klient jest uwierzytelniany przy użyciu certyfikatu X.509, otrzymuje tożsamości podstawowej, która składa się z nazwy podmiotu i odcisk palca certyfikatu.  
  
 Użyj <xref:System.Security.Permissions.PrincipalPermissionAttribute> do kontrolowania dostępu do zasobów na komputerze, na którym usługa jest uruchomiona, a jeśli użytkownicy usługi zawsze będzie częścią tej samej domeny Windows, czy usługa jest uruchomiona na. Możesz łatwo tworzyć grupy Windows, które zostały określone poziomy dostępu (np. Brak, tylko do odczytu lub odczytu i zapisu).  
  
 Aby uzyskać więcej informacji na temat za pomocą atrybutu zobacz [instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Aby uzyskać więcej informacji o tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Dostawcy członkostwa platformy ASP.NET  
 Funkcja [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jest dostawcy członkostwa. Mimo że dostawcy członkostwa, nie ma pod względem technicznym mechanizm kontroli dostępu, umożliwia kontrolowanie dostępu do usługi, ograniczając zestaw możliwych tożsamości, które mogą uzyskiwać dostęp do punktu końcowego usługi. Funkcja członkostwo obejmuje bazy danych, który można wypełnić przy użyciu kombinacji nazwy i hasła użytkownika, które umożliwiają użytkownikom witryny sieci Web zakładać kont w witrynie. Aby uzyskać dostęp do usługi, która używa dostawcy członkostwa, użytkownik musi zalogować się przy użyciu swojej nazwy użytkownika i hasło.  
  
> [!NOTE]
>  Najpierw należy wypełnić bazę danych za pomocą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcję, zanim usługa WCF można go użyć na potrzeby autoryzacji.  
  
 Umożliwia także funkcja członkostwa w członkowskiej bazie danych z istniejącego przypadku już [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web i chcesz włączyć tych samych użytkowników użyć usługi autoryzacji przy użyciu tej samej nazwy użytkownika i hasła.  
  
 Aby uzyskać więcej informacji na temat używania funkcji członkostwa w usłudze WCF zobacz [porady: użycie dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Dostawcy ról ASP.NET  
 Kolejną funkcją [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jest możliwość zarządzania autoryzacji przy użyciu ról. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy ról umożliwia deweloperów do tworzenia ról dla użytkowników i przypisać każdemu użytkownikowi na ról. Za pomocą dostawcy członkostwa, ról i przypisań są przechowywane w bazie danych i mogą zostać wypełnione za pomocą narzędzi dostarczonych przez określoną implementację [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról. Jako z funkcją członkostwa WCF deweloperzy mogą używać informacji w bazie danych do autoryzowania użytkowników usługi przez role. Na przykład można użyć dostawcy ról w połączeniu z `PrincipalPermissionAttribute` dostęp do mechanizmu kontroli opisanych powyżej.  
  
 Można również użyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, jeśli masz istniejącą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bazę danych dostawców ról, aby użyć tego samego zestawu reguł i przypisania użytkownika w usłudze WCF.  
  
 Aby uzyskać więcej informacji dotyczących używania funkcji dostawcy ról, zobacz [porady: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Menedżer autoryzacji  
 Kolejną funkcją łączy Menedżera autoryzacji (AzMan) z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, aby autoryzować klientów. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi sieci Web, AzMan można zintegrować aplikację tak, aby autoryzacji z usługą odbywa się za pośrednictwem AzMan hostów. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Menedżer ról zapewnia interfejs API, który pozwala na zarządzanie rolami w aplikacji, dodawania i usuwania użytkowników z ról oraz sprawdź członkostwo w roli, ale nie jest możliwe możesz zbadać, czy użytkownik jest autoryzowany do operacji lub nazwane zadanie. AzMan umożliwia definiowanie poszczególnych operacji i połączyć je w zadania. Za pomocą AZMan oprócz kontroli roli, możesz również sprawdzić czy użytkownik może wykonywać zadania. Autoryzacji ról przypisania i zadania można skonfigurowane poza aplikacją lub wykonać programowo w aplikacji. Administracja AzMan przystawkę Microsoft Management Console (MMC) umożliwia administratorom zmienić zadania, które rola może wykonywać w czasie wykonywania oraz zarządzanie członkostwem ról każdego użytkownika.  
  
 Możesz również użyć AzMan i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, jeśli już masz dostęp do istniejącej instalacji AzMan i chcesz autoryzować użytkowników usługi przy użyciu funkcji z połączenia dostawca AzMan/roli.  
  
 Aby uzyskać więcej informacji na temat AzMan i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, zobacz [instrukcje: Korzystanie z Menedżera autoryzacji (AzMan) za pomocą programu ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=88951). Aby uzyskać więcej informacji na temat przy użyciu AzMan i dostawcy ról, usług WCF zobacz [porady: Używanie dostawcy roli Menedżera autoryzacji platformy ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelu tożsamości  
 Model tożsamości to zestaw interfejsów API, które umożliwiają zarządzanie oświadczenia i zasady, aby autoryzować klientów. Za pomocą modelu tożsamości można sprawdzić, co oświadczeń zawartych w poświadczeniach, które pozwala uwierzytelniać w usłudze, porównywanie oświadczeń do zestawu zasad dla usługi i udzielić lub odmówić dostępu do obiektu wywołującego na podstawie porównania.  
  
 Jeśli potrzebujesz poprawnie kontrolę i możliwość ustawiania określone kryteria, zanim zostanie przyznany dostęp przy użyciu modelu tożsamości. Na przykład w przypadku korzystania z <xref:System.Security.Permissions.PrincipalPermissionAttribute>, kryterium jest po prostu, że tożsamość użytkownika jest uwierzytelniany i należy do określonej roli. Z kolei za pomocą modelu tożsamości, można utworzyć zasady, które użytkownik musi być ponad 18 lat i ma prawidłowe prawa jazdy przed uzyskaniem dostępu do wyświetlenia dokumentu.  
  
 Przykładem, w których możesz korzystać z modelu tożsamości kontrola dostępu oparta na oświadczeniach jest, gdy przy użyciu poświadczeń federacyjnych w scenariuszu wystawionych tokenów. Aby uzyskać więcej informacji na temat Federacja i wystawione tokeny, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Aby uzyskać więcej informacji na temat modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
