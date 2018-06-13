---
title: Mechanizmy kontroli dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 57ead53dd9e6bc1b2e3624791c7cc0c7d437cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493168"
---
# <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu
Można kontrolować dostęp w sposób kilka z usługi Windows Communication Foundation (WCF). W tym temacie pokrótce omówiono różne mechanizmy i sugestie dotyczące każdej; użycie ma ona ułatwiające wybranie poprawne mechanizm do użycia. Technologie dostępu są wymienione w kolejności złożoności. Najprostszą jest <xref:System.Security.Permissions.PrincipalPermissionAttribute>; najbardziej złożonych jest modelu tożsamości.  
  
 Oprócz tych mechanizmów, personifikacja i delegowanie z programem WCF zostało wyjaśnione w dokumencie [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Służy do ograniczania dostępu do metody usługi. Jeśli ten atrybut jest stosowany do metody, może służyć do żądania tożsamości obiektu wywołującego określonych lub członkostwa w grupie systemu Windows lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli. Jeśli klient zostanie uwierzytelniony za pomocą certyfikatu X.509, otrzymuje podstawowej tożsamości, która składa się z nazwy podmiotu i odcisk palca certyfikatu.  
  
 Użyj <xref:System.Security.Permissions.PrincipalPermissionAttribute> kontrolować dostęp do zasobów na komputerze, na którym usługa jest uruchomiona, a jeśli użytkownicy usługi zawsze będą częścią tej samej domeny systemu Windows, czy usługa jest uruchomiona na. Można jednak łatwo tworzyć grup systemu Windows, których określono poziomy dostępu (np. Brak, tylko do odczytu lub odczytu i zapisu).  
  
 Aby uzyskać więcej informacji na temat za pomocą atrybutu, zobacz [porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Aby uzyskać więcej informacji o tożsamości, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Dostawca członkostwa programu ASP.NET  
 Funkcja [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa. Nawet jeśli dostawca członkostwa nie jest technicznie mechanizmu kontroli dostępu, umożliwia kontrolowanie dostępu do usługi przez ograniczenie zestaw możliwych tożsamości, które mogą uzyskiwać dostęp do punktu końcowego usługi. Funkcja członkostwo obejmuje bazy danych, które można wypełniać za pomocą kombinacji nazwy i hasła użytkownika, które umożliwiają użytkownikom witryny sieci Web zakładać kont z lokacją. Aby uzyskać dostęp do usługi, która używa dostawcy członkostwa, użytkownik musi zalogować się ze swojej nazwy użytkownika i hasła.  
  
> [!NOTE]
>  Najpierw należy wypełnić w bazie danych przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji przed usługi WCF może być używany na potrzeby autoryzacji.  
  
 Umożliwia także funkcję członkostwa, jeśli masz już bazę danych z istniejącego członkostwa [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web i chcesz umożliwić użytkownikom tej samej do użycia z usługą autoryzacji o takiej samej nazwy użytkownika i hasła.  
  
 Aby uzyskać więcej informacji dotyczących używania funkcji członkostwa w usługi WCF, zobacz [porady: Używanie dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Dostawcy ról ASP.NET  
 Kolejną funkcją [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jest możliwość zarządzania autoryzację za pomocą ról. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy roli umożliwia deweloperów do tworzenia ról dla użytkowników i przypisać każdemu użytkownikowi do ról. Z dostawcy członkostwa, ról i przypisania są przechowywane w bazie danych i można wypełniać za pomocą narzędzi dostarczanych przez konkretnego implementacja [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról. Jako za pomocą funkcji członkostwa WCF deweloperzy mogą używać informacji w bazie danych do autoryzowania użytkowników usługi przez role. Na przykład można użyć dostawcy ról w połączeniu z `PrincipalPermissionAttribute` opisane powyżej mechanizm kontroli dostępu.  
  
 Można również użyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, jeśli masz istniejącą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bazy danych dostawcy roli, aby używać tego samego zestawu zasad i przypisań użytkownika w usłudze WCF.  
  
 Aby uzyskać więcej informacji dotyczących używania funkcji dostawcy ról, zobacz [porady: Używanie dostawcy ról ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Menedżer autoryzacji  
 Inna funkcja łączy Menedżera autoryzacji (AzMan) z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, aby zezwolić klientom. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi sieci Web, AzMan można zintegrować aplikacji tak, aby autoryzacji do usługi odbywa się za pośrednictwem AzMan hostów. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Menedżer ról zapewnia interfejs API, który umożliwia zarządzanie rolami aplikacji, dodawać i usuwać użytkowników z ról i sprawdź członkostwo roli, ale nie zezwala na zapytanie, czy użytkownik jest autoryzowany do wykonania operacji lub zadań o nazwie. AzMan umożliwia definiowanie poszczególnych działań i połączyć je w zadania. Z AZMan oprócz kontroli roli można również sprawdzić, czy użytkownik może wykonywać zadania. Przypisania i zadania autoryzacji ról można skonfigurować lokalizację poza aplikacją lub wykonać programowo w aplikacji. Administracja AzMan przystawki programu Microsoft Management Console (MMC) pozwala administratorom zmiana roli można wykonywać w czasie wykonywania zadań oraz zarządzanie członkostwem ról każdego użytkownika.  
  
 Można również użyć AzMan i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, jeśli już masz dostęp do istniejącej instalacji AzMan, a chcesz zezwolić użytkownikom usługi przy użyciu funkcji kombinacja dostawcy AzMan/roli.  
  
 Aby uzyskać więcej informacji na temat AzMan i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, zobacz [jak: Korzystanie z Menedżera autoryzacji (AzMan) z programem ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=88951). Aby uzyskać więcej informacji o używaniu AzMan i dostawca ról dla usług WCF, zobacz [porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelu tożsamości  
 Modelu tożsamości to zestaw interfejsów API, które umożliwiają zarządzanie oświadczeń i zasad, aby zezwolić klientom. W modelu tożsamości można sprawdzić co oświadczeń zawartych w poświadczenia, które wywołującego używany do samodzielnego uwierzytelnienia usługi, porównaj oświadczenia do zestawu zasad dla usługi i Udziel lub Odmów dostępu na podstawie porównania.  
  
 Użyj modelu tożsamości, jeśli konieczne drobne możliwość określenia kryteriów określonych przed udzieleniem im dostępu i kontroli. Na przykład w przypadku korzystania z <xref:System.Security.Permissions.PrincipalPermissionAttribute>, kryterium jest po prostu tożsamości użytkownika jest uwierzytelniana, a należy do określonej roli. Z kolei za pomocą modelu tożsamości, można utworzyć zasad, użytkownik musi być ponad 18 roku życia i posiada nieprawidłowy sterownik licencji przed uzyskaniem dostępu do wyświetlania dokumentu.  
  
 Przykładem, w której będzie można korzystać z kontroli dostępu na podstawie oświadczeń modelu tożsamości jest korzystając z poświadczeń federacyjnych w scenariuszu wystawionego tokenu. Aby uzyskać więcej informacji na temat Federacja i wystawione tokeny, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Aby uzyskać więcej informacji na temat modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
