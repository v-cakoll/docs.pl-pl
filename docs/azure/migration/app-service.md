---
title: Migrowanie usługi lub aplikacji sieci Web platformy .NET do Azure App Service
description: Dowiedz się więcej na temat migrowania usługi lub aplikacji sieci Web platformy .NET ze środowiska lokalnego do Azure App Service.
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: d208865942b49ae2d5437b8f2fcff294933af21b
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174312"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Migrowanie usługi lub aplikacji sieci Web platformy .NET do Azure App Service

[App Service](/azure/app-service/overview) to w pełni zarządzana usługa platformy obliczeniowej, zoptymalizowana pod kątem hostingu skalowalnych witryn internetowych i aplikacji sieci Web. Ten artykuł zawiera informacje na temat sposobu podnoszenia i przenoszenia istniejącej aplikacji do Azure App Service, modyfikacji i dodatkowych zasobów związanych z [przechodzeniem do chmury](https://azure.microsoft.com/migration/web-applications/). Większość ASP.NETych witryn internetowych (WebForms, MVC) i usług (Web API, WCF) można przenieść bezpośrednio do Azure App Service bez zmian. Niektóre mogą wymagać drobnych zmian, podczas gdy inne mogą wymagać refaktoryzacji.

Chcesz zacząć? [Opublikuj aplikację ASP.NET + SQL, aby Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Kwestie do rozważenia

### <a name="on-premises-resources-including-sql-server"></a>Zasoby lokalne (w tym SQL Server)

Sprawdź dostęp do zasobów lokalnych, ponieważ może być konieczne ich Migrowanie lub zmiana. Poniżej przedstawiono opcje ograniczania dostępu do zasobów lokalnych:

* Tworzenie sieci VPN łączącej App Service z zasobami lokalnymi przy użyciu [sieci wirtualnych platformy Azure](/azure/app-service/web-sites-integrate-with-vnet).
* Bezpieczne udostępnianie usług lokalnych w chmurze bez konieczności zmiany zapory przy użyciu [Azure Relay](/azure/service-bus-relay/relay-what-is-it).
* Migruj zależności, takie jak [baza danych SQL](https://go.microsoft.com/fwlink/?linkid=863217) , na platformę Azure.
* Użyj ofert typu "platforma jako usługa" w chmurze, aby zmniejszyć zależności. Na przykład zamiast nawiązywać połączenia z lokalnym serwerem poczty należy rozważyć użycie [SendGrid](/azure/sendgrid-dotnet-how-to-send-email).

### <a name="port-bindings"></a>Powiązania portów

Azure App Service obsługuje port 80 dla protokołu HTTP i portu 443 dla ruchu HTTPS.

W przypadku programu WCF obsługiwane są następujące powiązania:

| Wiązanie | Uwagi |
|--|--|
| `BasicHttp` |  |
| `WSHttp` |  |
| `WSDualHttpBinding` | Należy włączyć [obsługę gniazda sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-configure) . | Należy włączyć [obsługę gniazda sieci Web](/azure/app-service/web-sites-configure) . |
| `NetHttpBinding` | [Obsługa gniazd sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-configure) musi być włączona dla umów dupleksowych. | [Obsługa gniazd sieci Web](/azure/app-service/web-sites-configure) musi być włączona dla umów dupleksowych. |
| `NetHttpsBinding` | [Obsługa gniazd sieci Web](https://docs.microsoft.com/azure/app-service/web-sites-configure) musi być włączona dla umów dupleksowych. | [Obsługa gniazd sieci Web](/azure/app-service/web-sites-configure) musi być włączona dla umów dupleksowych. |
| `BasicHttpContextBinding` |  |
| `WebHttpBinding` |  |
| `WSHttpContextBinding` |  |

### <a name="authentication"></a>Uwierzytelnianie

Azure App Service domyślnie obsługuje uwierzytelnianie anonimowe i uwierzytelnianie formularzy, gdy zamierzone. Uwierzytelnianie systemu Windows może być używane przez integrację z usługami Azure Active Directory i ADFS. [Dowiedz się więcej na temat integrowania katalogów lokalnych z Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Zestawy w pamięci podręcznej GAC (globalna pamięć podręczna zestawów)

Ta funkcja nie jest obsługiwana. Rozważ skopiowanie wymaganych zestawów do folderu *\Bin* aplikacji. Nie można używać niestandardowych plików *. msi* zainstalowanych na serwerze (na przykład generatorów PDF).

### <a name="iis-settings"></a>Ustawienia usług IIS

Wszystkie tradycyjnie skonfigurowane za pośrednictwem applicationHost.config w aplikacji można teraz skonfigurować za pośrednictwem Azure Portal. Dotyczy to puli aplikacji bitów, włączania/wyłączania obiektów WebSockets, zarządzanej wersji potoku, wersji .NET Framework (2.0/4.0) itd. Aby zmodyfikować [Ustawienia aplikacji](/azure/app-service/web-sites-configure), przejdź do [Azure Portal](https://portal.azure.com), Otwórz blok aplikacji sieci Web, a następnie wybierz kartę **Ustawienia aplikacji** .

#### <a name="iis5-compatibility-mode"></a>Tryb zgodności wersją IIS5

Tryb zgodności wersją IIS5 nie jest obsługiwany. W Azure App Service każda aplikacja sieci Web i wszystkie znajdujące się w niej aplikacje działają w tym samym procesie roboczym z określonym zestawem [pul aplikacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)).

#### <a name="iis7-schema-compliance"></a>Zgodność schematu IIS7 +

Niektóre elementy i atrybuty nie są zdefiniowane w schemacie Azure App Service IIS. Jeśli wystąpią problemy, rozważ użycie [transformacji XDT](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).

#### <a name="single-application-pool-per-site"></a>Jedna pula aplikacji na lokację

W Azure App Service każda aplikacja sieci Web i wszystkie znajdujące się w niej aplikacje są uruchamiane w tej samej puli aplikacji. Rozważ utworzenie jednej puli aplikacji z typowymi ustawieniami lub utworzenie oddzielnej aplikacji sieci Web dla każdej aplikacji.

### <a name="com-and-com-components"></a>Składniki COM i COM+

Azure App Service nie zezwala na rejestrację składników COM na platformie. Jeśli aplikacja korzysta z dowolnego składnika modelu COM, muszą one być ponownie zapisywane w kodzie zarządzanym i wdrażane z witryną lub aplikacją.

### <a name="physical-directories"></a>Katalogi fizyczne

Azure App Service nie zezwala na dostęp do dysku fizycznego. Może być konieczne użycie [Azure Files](/azure/storage/files/storage-files-introduction) , aby uzyskać dostęp do plików za pośrednictwem protokołu SMB. [Usługa Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) może przechowywać pliki do dostępu za pośrednictwem protokołu HTTPS.

### <a name="isapi-filters"></a>Filtry ISAPI

Azure App Service może obsługiwać korzystanie z filtrów ISAPI, jednak biblioteka ISAPI DLL musi być wdrożona z lokacją i zarejestrowana za pośrednictwem web.config.

### <a name="https-bindings-and-ssl"></a>Powiązania HTTPS i SSL

Powiązania HTTPS nie są migrowane ani nie są skojarzone z witrynami sieci Web. Po zakończeniu migracji lokacji [można ręcznie przekazać certyfikaty SSL](/azure/app-service/app-service-web-tutorial-custom-ssl) .

### <a name="sharepoint-and-frontpage"></a>SharePoint i FrontPage

Programy SharePoint i rozszerzenia FrontPage Server Extensions (FPSE) nie są obsługiwane.

### <a name="web-site-size"></a>Rozmiar witryny sieci Web

Dla bezpłatnych witryn obowiązuje limit rozmiaru równy 1 GB. Jeśli witryna jest dłuższa niż 1 GB, należy przeprowadzić uaktualnienie do płatnej jednostki SKU. Zobacz [cennik App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="database-size"></a>Rozmiar bazy danych

W przypadku baz danych SQL Server Sprawdź bieżące [SQL Database cennika](https://azure.microsoft.com/pricing/details/sql-database).

### <a name="azure-active-directory-aad-integration"></a>Integracja z usługą Azure Active Directory (AAD)

Usługa AAD nie współpracuje z bezpłatnymi aplikacjami. Aby korzystać z usługi AAD, należy uaktualnić jednostkę SKU aplikacji. Zobacz [cennik App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Monitorowanie i diagnostyka

Twoje bieżące rozwiązania lokalne na potrzeby monitorowania i diagnostyki prawdopodobnie nie będą działały w chmurze. Jednak platforma Azure oferuje narzędzia do rejestrowania, monitorowania i diagnostyki, dzięki czemu można identyfikować i debugować problemy z aplikacjami sieci Web. Możesz łatwo włączyć diagnostykę dla aplikacji sieci Web w swojej konfiguracji, a także wyświetlić dzienniki zarejestrowane w usłudze Azure Application Insights. [Dowiedz się więcej na temat włączania rejestrowania diagnostycznego dla aplikacji sieci Web](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Parametry połączenia i ustawienia aplikacji

Rozważ użycie [magazynu kluczy platformy Azure](/azure/key-vault/)— usługi, która bezpiecznie przechowuje poufne informacje używane w aplikacji. Alternatywnie można zapisać te dane jako ustawienie App Service.

### <a name="dns"></a>DNS

Może być konieczne zaktualizowanie konfiguracji DNS na podstawie wymagań aplikacji. Te ustawienia DNS można skonfigurować w App Service [niestandardowych ustawień domeny](/azure/app-service/app-service-web-tutorial-custom-domain).

## <a name="azure-app-service-with-windows-containers"></a>Azure App Service z kontenerami systemu Windows

Jeśli nie można migrować aplikacji bezpośrednio do App Service, należy rozważyć App Service przy użyciu kontenerów systemu Windows, które umożliwiają użycie GAC, składników COM, MSIs, pełny dostęp do interfejsów API programu .NET FX, DirectX i innych.

## <a name="see-also"></a>Zobacz też

* [Jak określić, czy aplikacja kwalifikuje się do App Service](https://appmigration.microsoft.com/)
* [Przeniesienie bazy danych do chmury](sql.md)
* [Szczegóły i ograniczenia piaskownicy aplikacji sieci Web platformy Azure](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
