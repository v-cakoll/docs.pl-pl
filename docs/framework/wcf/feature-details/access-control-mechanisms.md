---
title: Mechanizmy kontroli dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185495"
---
# <a name="access-control-mechanisms"></a>Mechanizmy kontroli dostępu
Dostęp można kontrolować w kilka sposobów za pomocą programu Windows Communication Foundation (WCF). W tym temacie pokrótce omówiono różne mechanizmy i zawiera sugestie, kiedy używać każdego; ma na celu pomóc w wyborze odpowiedniego mechanizmu do użycia. Technologie dostępu są wymienione w kolejności złożoności. Najprostszym <xref:System.Security.Permissions.PrincipalPermissionAttribute>jest ; najbardziej złożony jest model tożsamości.  
  
 Oprócz tych mechanizmów, personifikacji i delegowania z WCF jest wyjaśnione w [delegowania i personifikacji](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 Jest <xref:System.Security.Permissions.PrincipalPermissionAttribute> używany do ograniczania dostępu do metody usługi. Gdy atrybut jest stosowany do metody, może służyć do żądania tożsamości określonego obiektu wywołującego lub członkostwa w grupie systemu Windows lub ASP.NET roli. Jeśli klient jest uwierzytelniany przy użyciu certyfikatu X.509, otrzymuje podstawową tożsamość, która składa się z nazwy podmiotu oraz odcisk palca certyfikatu.  
  
 Służy <xref:System.Security.Permissions.PrincipalPermissionAttribute> do kontrolowania dostępu do zasobów na komputerze, na którego jest uruchomiona usługa, a użytkownicy usługi zawsze będą częścią tej samej domeny systemu Windows, na której jest uruchomiona usługa. Można łatwo tworzyć grupy systemu Windows, które mają określony poziom dostępu (na przykład brak, tylko do odczytu lub odczyt i zapis).  
  
 Aby uzyskać więcej informacji na temat korzystania z atrybutu, zobacz [Jak: Ogranicz dostęp z PrincipalPermissionAttribute Klasy](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Aby uzyskać więcej informacji na temat tożsamości, zobacz [Tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Dostawca członkostwa ASP.NET  
 Cechą ASP.NET jest dostawca członkostwa. Mimo że dostawca członkostwa nie jest technicznie mechanizm kontroli dostępu, umożliwia kontrolowanie dostępu do usługi, ograniczając zestaw możliwych tożsamości, które mogą uzyskać dostęp do punktu końcowego usługi. Funkcja członkostwa obejmuje bazę danych, która może być wypełniona kombinacjami nazw użytkowników i haseł, które umożliwiają użytkownikom witryny sieci Web tworzenie kont w witrynie. Aby uzyskać dostęp do usługi korzystającej z dostawcy członkostwa, użytkownik musi zalogować się przy użyciu nazwy użytkownika i hasła.  
  
> [!NOTE]
> Należy najpierw wypełnić bazę danych przy użyciu funkcji ASP.NET, zanim usługa WCF może używać jej do celów autoryzacji.  
  
 Funkcji członkostwa można również użyć, jeśli masz już bazę danych członkostwa z istniejącej witryny sieci Web ASP.NET i chcesz włączyć tych samych użytkowników do korzystania z usługi, autoryzowanej z tymi samymi nazwami użytkowników i hasłami.  
  
 Aby uzyskać więcej informacji na temat korzystania z funkcji członkostwa w usłudze WCF, zobacz [Jak: Korzystanie z dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Dostawca roli ASP.NET  
 Inną cechą ASP.NET jest możliwość zarządzania autoryzacją przy użyciu ról. Dostawca roli ASP.NET umożliwia deweloperowi tworzenie ról dla użytkowników i przypisywanie każdego użytkownika do roli lub ról. Podobnie jak w przypadku dostawcy członkostwa, role i przydziały są przechowywane w bazie danych i mogą być wypełniane przy użyciu narzędzi dostarczonych przez określoną implementację dostawcy roli ASP.NET. Podobnie jak w przypadku funkcji członkostwa, deweloperzy WCF można użyć informacji w bazie danych do autoryzowania użytkowników usługi według ról. Mogą one, na przykład, używać dostawcy `PrincipalPermissionAttribute` roli w połączeniu z mechanizmem kontroli dostępu opisanych powyżej.  
  
 Można również użyć dostawcy roli ASP.NET, jeśli masz istniejącą bazę danych dostawcy ról ASP.NET i chcesz użyć tego samego zestawu reguł i przypisań użytkowników w usłudze WCF.  
  
 Aby uzyskać więcej informacji na temat korzystania z funkcji dostawcy roli, zobacz [Jak: Korzystanie z ASP.NET dostawcy roli z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Menedżer autoryzacji  
 Inna funkcja łączy Menedżera autoryzacji (AzMan) z dostawcą roli ASP.NET do autoryzowania klientów. Gdy ASP.NET hostuje usługę sieci Web, AzMan można zintegrować z aplikacją, dzięki czemu autoryzacja usługi odbywa się za pośrednictwem azmanu. ASP.NET menedżer ról udostępnia interfejs API, który umożliwia zarządzanie rolami aplikacji, dodawanie i usuwanie użytkowników z ról i sprawdzanie członkostwa roli, ale nie pozwala na wykonywanie nazwanych zadań lub operacji. AzMan pozwala zdefiniować poszczególne operacje i połączyć je w zadania. Z AZMan, oprócz sprawdzania roli, można również sprawdzić, czy użytkownik może wykonać zadanie. Przypisywanie ról i autoryzacja zadań można skonfigurować poza aplikacją lub wykonać programowo w aplikacji. Przystawka AzMan administracji Programu Microsoft Management Console (MMC) umożliwia administratorom zmianę zadań, które rola może wykonywać w czasie wykonywania i zarządzanie członkostwem ról każdego użytkownika.  
  
 Można również użyć AzMan i dostawcy roli ASP.NET, jeśli masz już dostęp do istniejącej instalacji AzMan i chcesz autoryzować użytkowników usługi przy użyciu funkcji kombinacji AzMan/dostawca roli.  
  
 Aby uzyskać więcej informacji na temat programu AzMan i dostawcy roli ASP.NET, zobacz [Jak: Użyj Menedżera autoryzacji (AzMan) z ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)). Aby uzyskać więcej informacji na temat korzystania z programu AzMan i dostawcy roli dla usług WCF, zobacz [Jak: Korzystanie z dostawcy roli menedżera autoryzacji ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Model tożsamości  
 Model tożsamości to zestaw interfejsów API, które umożliwiają zarządzanie oświadczeniami i zasadami autoryzowania klientów. Za pomocą modelu tożsamości można sprawdzić każde oświadczenie zawarte w poświadczeniach, które wywołujący używany do uwierzytelniania się do usługi, porównać oświadczenia z zestawem zasad dla usługi i udzielić lub odmówić dostępu na podstawie porównania.  
  
 Użyj modelu tożsamości, jeśli potrzebujesz precyzyjnej kontroli i możliwości ustawiania określonych kryteriów przed udzieleniem dostępu. Na przykład podczas <xref:System.Security.Permissions.PrincipalPermissionAttribute>korzystania z kryterium , kryterium jest po prostu, że tożsamość użytkownika jest uwierzytelniony i należy do określonej roli. Z drugiej strony za pomocą modelu tożsamości można utworzyć zasady, która stanowi, że użytkownik musi mieć więcej niż 18 lat i posiada ważne prawo jazdy przed zezwoleniem na wyświetlanie dokumentu.  
  
 Jednym z przykładów, gdzie można korzystać z kontroli dostępu opartej na oświadczenia modelu tożsamości jest podczas korzystania z poświadczeń federacji w scenariuszu wystawionego tokenu. Aby uzyskać więcej informacji na temat federacji i wystawionych tokenów, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Aby uzyskać więcej informacji na temat modelu tożsamości, zobacz [Zarządzanie roszczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
