---
title: Migrowanie aplikacji lub usługi sieci Web platformy .NET do usługi Azure App Service
description: Dowiedz się więcej o migrowaniu aplikacji lub usługi sieci web platformy .NET z lokalnego do usługi Azure App Service.
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 57f3b981a1d94c2193160f55f9c8242da694c169
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072138"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Migrowanie aplikacji lub usługi sieci Web platformy .NET do usługi Azure App Service

[App Service](https://docs.microsoft.com/azure/app-service/overview) to w pełni zarządzana usługa platformy obliczeniowej zoptymalizowana pod kątem hostingu skalowalnych witryn sieci Web i aplikacji sieci Web. Ten artykuł zawiera informacje dotyczące sposobu podnoszenia i przenoszenia istniejącej aplikacji do usługi Azure App Service, modyfikacji do rozważenia i dodatkowych zasobów [do przenoszenia do chmury.](https://azure.microsoft.com/migration/web-applications/) Większość ASP.NET witrynach sieci Web (Webforms, MVC) i usług (Web API, WCF) można przejść bezpośrednio do usługi Azure App Service bez żadnych zmian. Niektóre mogą wymagać drobnych zmian, podczas gdy inne mogą wymagać refaktoryzacji.

Chcesz zacząć? [Opublikuj swoją ASP.NET + aplikację SQL w usłudze Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Zagadnienia do rozważenia

### <a name="on-premises-resources-including-sql-server"></a>Zasoby lokalne (w tym program SQL Server)

Sprawdź dostęp do zasobów lokalnych, ponieważ mogą one wymagać migracji lub zmiany. Poniżej przedstawiono opcje ograniczania dostępu do zasobów lokalnych:

* Utwórz usługę VPN łączącą usługę App Service z zasobami lokalnymi przy użyciu [sieci wirtualnych platformy Azure](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet).
* Bezpiecznie udostępniaj usługi lokalne w chmurze bez zmian zapory za pomocą [usługi Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).
* Migrowanie zależności, takich jak [baza danych SQL](https://go.microsoft.com/fwlink/?linkid=863217) na platformę Azure.
* Użyj oferty platformy jako usługi w chmurze, aby zmniejszyć zależności. Na przykład zamiast łączyć się z lokalnym serwerem poczty, należy rozważyć użycie [sendgrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email).

### <a name="port-bindings"></a>Powiązania portów

Usługa Azure App Service obsługuje port 80 dla protokołu HTTP i port 443 dla ruchu HTTPS.

Dla WCF obsługiwane są następujące powiązania:

Wiązanie | Uwagi
--------|--------
Podstawowehttp |
WSHttp |
WSDualHttpBinowanie | [Obsługa gniazd internetowych](https://docs.microsoft.com/azure/app-service/web-sites-configure) musi być włączona.
NetHttpBinding | [Obsługa gniazd sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-configure) musi być włączona dla kontraktów dupleksowych.
NetHttpsBinding (NetHttpsBinding) | [Obsługa gniazd sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-configure) musi być włączona dla kontraktów dupleksowych.
Podstawowe powiązaniehttpHttpContextBinding |
Powiązaniehttpa sieci Web |
WSHttpContextBinding |

### <a name="authentication"></a>Authentication

Usługa Azure App Service domyślnie obsługuje uwierzytelnianie anonimowe i uwierzytelnianie formularzy, gdy jest to zamierzone. Uwierzytelnianie systemu Windows może być używane tylko przez integrację z usługą Azure Active Directory i usługą ADFS. [Dowiedz się więcej o integrowanie katalogów lokalnych z usługą Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Zestawy w pamięci podręcznej GAC (globalna pamięć podręczna zestawów)

Ta funkcja nie jest obsługiwana. Należy rozważyć skopiowanie wymaganych zestawów do folderu *\bin* aplikacji. Nie można używać niestandardowych plików *msi* zainstalowanych na serwerze (na przykład generatorów PDF).

### <a name="iis-settings"></a>Ustawienia iis
Wszystko tradycyjnie skonfigurowane za pośrednictwem aplikacjiHost.config w aplikacji można teraz skonfigurować za pośrednictwem witryny Azure portal. Dotyczy to bitupula apppool, enable/disable WebSockets, wersji zarządzanego potoku, wersji .NET Framework (2.0/4.0) i tak dalej. Aby zmodyfikować [ustawienia aplikacji,](https://docs.microsoft.com/azure/app-service/web-sites-configure)przejdź do [witryny Azure Portal](https://portal.azure.com), otwórz blok dla aplikacji sieci web, a następnie wybierz kartę Ustawienia **aplikacji.**

#### <a name="iis5-compatibility-mode"></a>Tryb zgodności z programem IIS5
Tryb zgodności iis5 nie jest obsługiwany. W usłudze Azure App Service każda aplikacja sieci Web i wszystkie aplikacje w ramach niej są uruchamiane w tym samym procesie roboczym z określonym zestawem [pul aplikacji.](https://technet.microsoft.com/library/cc735247(v=WS.10).aspx)

#### <a name="iis7-schema-compliance"></a>Zgodność schematu usług IIS7+  
Niektóre elementy i atrybuty nie są zdefiniowane w schemacie usług IIS usługi Azure App Service. Jeśli wystąpią problemy, należy rozważyć użycie [XDT transformacji](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).

#### <a name="single-application-pool-per-site"></a>Pula pojedynczych aplikacji na witrynę  
W usłudze Azure App Service każda aplikacja sieci web i wszystkie aplikacje w obszarze niego są uruchamiane w tej samej puli aplikacji. Należy rozważyć ustanowienie puli pojedynczej aplikacji z typowymi ustawieniami lub utworzenie oddzielnej aplikacji sieci web dla każdej aplikacji.

### <a name="com-and-com-components"></a>Komponenty COM i COM+  
Usługa Azure App Service nie zezwala na rejestrację składników COM na platformie. Jeśli aplikacja korzysta z dowolnych składników COM, należy je przepisać w kodzie zarządzanym i wdrożyć w witrynie lub aplikacji.

### <a name="physical-directories"></a>Katalogi fizyczne
Usługa Azure App Service nie zezwala na dostęp do dysków fizycznych. Może być konieczne użycie [usługi Azure Files,](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) aby uzyskać dostęp do plików za pośrednictwem protokołu SMB. [Usługa Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) może przechowywać pliki w celu uzyskania dostępu za pośrednictwem protokołu HTTPS.

### <a name="isapi-filters"></a>Filtry ISAPI  
Usługa Azure App Service może obsługiwać korzystanie z filtrów ISAPI, jednak biblioteka DLL ISAPI musi zostać wdrożona w witrynie i zarejestrowana za pośrednictwem witryny web.config.

### <a name="https-bindings-and-ssl"></a>Powiązania HTTPS i protokół SSL
Powiązania HTTPS nie są migrowane ani certyfikaty SSL skojarzone z witrynami sieci web. [Certyfikaty SSL można](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl) jednak ręcznie przekazać po zakończeniu migracji do witryny.

### <a name="sharepoint-and-frontpage"></a>Program SharePoint i program FrontPage
Rozszerzenia programu SharePoint i programu FrontPage Server (FPSE) nie są obsługiwane.

### <a name="web-site-size"></a>Rozmiar witryny sieci Web  
Darmowe witryny mają limit rozmiaru 1 GB zawartości. Jeśli witryna jest większa niż 1 GB, należy uaktualnić do płatnej jednostki SKU. Zobacz [Ceny usługi App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="database-size"></a>Rozmiar bazy danych  
W przypadku baz danych programu SQL Server sprawdź aktualne [ceny bazy danych SQL](https://azure.microsoft.com/pricing/details/sql-database).

### <a name="azure-active-directory-aad-integration"></a>Integracja z usługą Azure Active Directory (AAD)  
AAD nie działa z darmowymi aplikacjami. Aby korzystać z funkcji AAD, należy uaktualnić jednostkę SKU aplikacji. Zobacz [Ceny usługi App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Monitorowanie i diagnostyka
Bieżące rozwiązania lokalne do monitorowania i diagnostyki są mało prawdopodobne, aby działać w chmurze. Jednak platforma Azure udostępnia narzędzia do rejestrowania, monitorowania i diagnostyki, dzięki czemu można zidentyfikować i debugować problemy z aplikacjami sieci web. Można łatwo włączyć diagnostykę aplikacji sieci web w jej konfiguracji i można wyświetlić dzienniki zarejestrowane w usłudze Azure Application Insights. [Dowiedz się więcej o włączaniu rejestrowania diagnostyki dla aplikacji sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Parametry połączenia i ustawienia aplikacji
Należy rozważyć użycie [usługi Azure KeyVault](https://docs.microsoft.com/azure/key-vault/), usługi, która bezpiecznie przechowuje poufne informacje używane w aplikacji. Alternatywnie można przechowywać te dane jako ustawienie usługi app service.

### <a name="dns"></a>DNS
Może być konieczne zaktualizowanie konfiguracji DNS na podstawie wymagań aplikacji. Te ustawienia DNS można skonfigurować w [niestandardowych ustawieniach domeny](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)usługi App Service .

## <a name="azure-app-service-with-windows-containers"></a>Usługa Azure App Service z kontenerami systemu Windows
Jeśli aplikacji nie można przeprowadzić migracji bezpośrednio do usługi App Service, należy wziąć pod uwagę usługi App Service przy użyciu kontenerów systemu Windows, który umożliwia korzystanie z gac, składniki COM, MSI, pełny dostęp do interfejsów API .NET FX, DirectX i więcej.

## <a name="see-also"></a>Zobacz też

* [Jak ustalić, czy aplikacja kwalifikuje się do usługi App Service](https://appmigration.microsoft.com/)
* [Przenoszenie bazy danych do chmury](https://go.microsoft.com/fwlink/?linkid=863217)
* [Szczegóły i ograniczenia piaskownicy aplikacji sieci Web platformy Azure](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
