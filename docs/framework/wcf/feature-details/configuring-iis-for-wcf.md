---
title: Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664621"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="93fc1-102">Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="93fc1-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="93fc1-103">Usług informacje internetowe (IIS) 7.0 ma modułowej, która umożliwia selektywną instalację składników, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="93fc1-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="93fc1-104">Projekt będzie opierać się na nowej technologii oparte na manifeście componentization wprowadzona w [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93fc1-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="93fc1-105">Istnieje więcej niż 40 autonomiczny składników funkcji usług IIS 7.0, którą można zainstalować niezależnie.</span><span class="sxs-lookup"><span data-stu-id="93fc1-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="93fc1-106">Dzięki temu specjaliści IT mogą więc łatwo dostosować instalację zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="93fc1-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="93fc1-107">W tym temacie omówiono sposób konfigurowania usług IIS 7.0 do użycia przy użyciu programu Windows Communication Foundation (WCF) i określić, które składniki są wymagane.</span><span class="sxs-lookup"><span data-stu-id="93fc1-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="93fc1-108">Minimalnej instalacji: Instalowanie WAS</span><span class="sxs-lookup"><span data-stu-id="93fc1-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="93fc1-109">Minimalnej instalacji cały pakiet usług IIS 7.0 polega na zainstalowaniu Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="93fc1-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="93fc1-110">BYŁ to funkcja autonomiczne i jest jedyną funkcją z usług IIS 7.0, który jest dostępny dla wszystkich [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów operacyjnych (Home Basic, Home Premium, firm i Ultimate i Enterprise).</span><span class="sxs-lookup"><span data-stu-id="93fc1-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="93fc1-111">W Panelu sterowania kliknij **programy** a następnie kliknij przycisk **Windows Włącz lub wyłącz funkcje** wymienionych w obszarze **programy i funkcje**, składnik WAS jest wyświetlany w Lista, tak jak na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="93fc1-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="93fc1-112">![Włączanie funkcji lub wyłącz okna dialogowego](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="93fc1-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="93fc1-113">Ta funkcja obejmuje następujące składniki podrzędne:</span><span class="sxs-lookup"><span data-stu-id="93fc1-113">This feature has the following sub-components:</span></span>

-   <span data-ttu-id="93fc1-114">Środowisko .NET</span><span class="sxs-lookup"><span data-stu-id="93fc1-114">.NET Environment</span></span>

-   <span data-ttu-id="93fc1-115">Interfejsy API konfiguracji</span><span class="sxs-lookup"><span data-stu-id="93fc1-115">Configuration APIs</span></span>

-   <span data-ttu-id="93fc1-116">Model procesów</span><span class="sxs-lookup"><span data-stu-id="93fc1-116">Process Model</span></span>

 <span data-ttu-id="93fc1-117">Jeśli wybierzesz węzeł główny WAS, tylko **Model procesu** węzeł podrzędny jest zaznaczone domyślnie.</span><span class="sxs-lookup"><span data-stu-id="93fc1-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="93fc1-118">Należy pamiętać, że tej instalacji tylko instalacja WAS, ponieważ nie jest obsługiwane dla serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="93fc1-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="93fc1-119">Aby upewnić się, WCF i wszelkie prace aplikacji ASP.NET, sprawdź **środowiska .NET** pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="93fc1-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="93fc1-120">Oznacza to, czy wszystkie składniki WAS wymagane dokonanie WCF i platforma ASP.NET, aby działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="93fc1-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="93fc1-121">Są one automatycznie sprawdzane, po zainstalowaniu dowolnego z tych składników.</span><span class="sxs-lookup"><span data-stu-id="93fc1-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="93fc1-122">Usługi IIS 7.0: Instalacja domyślna</span><span class="sxs-lookup"><span data-stu-id="93fc1-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="93fc1-123">Sprawdzając **Internetowe usługi informacyjne** funkcji, niektóre węzły podrzędne są automatycznie sprawdzane, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="93fc1-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="93fc1-124">![Domyślne ustawienia funkcji usług IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="93fc1-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="93fc1-125">Jest to domyślna instalacja usług IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="93fc1-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="93fc1-126">Za pomocą tej instalacji usług IIS 7.0 służy również do zawartości statycznej usługi (takie jak strony HTML i innej zawartości).</span><span class="sxs-lookup"><span data-stu-id="93fc1-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="93fc1-127">Jednak nie można uruchomić aplikacji ASP.NET i CGI lub hosta usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="93fc1-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="93fc1-128">Usługi IIS 7.0: Instalacji z obsługą platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="93fc1-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="93fc1-129">Należy zainstalować program ASP.NET, aby ASP.NET działa przez usługi IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="93fc1-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="93fc1-130">Po sprawdzeniu **ASP.NET**, ekran powinien wyglądać podobnie do poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="93fc1-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="93fc1-131">![Asp.NET wymagane ustawienia](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="93fc1-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="93fc1-132">Jest to minimalne środowisko dla aplikacji ASP.NET i WCF do pracy w usługach IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="93fc1-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="93fc1-133">Usługi IIS 7.0: Instalacji za pomocą usług IIS 6.0 zgodności składników</span><span class="sxs-lookup"><span data-stu-id="93fc1-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="93fc1-134">Podczas instalowania usług IIS 7.0 w systemie przy użyciu programu Visual Studio 2005 lub niektóre skrypty automatyzacji lub narzędzia (takie jak Adsutil.vbs), skonfigurowanych przez wirtualne aplikacje, które używają interfejsu API programu IIS 6.0 metabazy, upewnij się, sprawdzenie, czy usługi IIS 6.0 **narzędzia obsługi skryptów**.</span><span class="sxs-lookup"><span data-stu-id="93fc1-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="93fc1-135">To automatycznie sprawdza, czy innych węzłów podrzędnych usług IIS 6.0 **zgodność z narzędziami zarządzania**.</span><span class="sxs-lookup"><span data-stu-id="93fc1-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="93fc1-136">Na poniższej ilustracji przedstawiono ekran po tej operacji:</span><span class="sxs-lookup"><span data-stu-id="93fc1-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="93fc1-137">![Ustawienia zgodności programu IIS 6.0 zarządzania](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="93fc1-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="93fc1-138">Dzięki tej instalacji masz wszystko, co jest wymagane, aby korzystać z funkcji usług IIS 7.0, ASP.NET i WCF i przykładów dostępnych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="93fc1-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="93fc1-139">Limity żądań</span><span class="sxs-lookup"><span data-stu-id="93fc1-139">Request Limits</span></span>
 <span data-ttu-id="93fc1-140">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] za pomocą usług IIS 7, wartość domyślna elementu `maxUri` i `maxQueryStringSize` ustawienia zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="93fc1-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="93fc1-141">Domyślnie filtrowania żądań w usługach IIS 7.0 umożliwia długości adresu URL 4096 znaków i długość ciągu zapytania, 2048 znaków.</span><span class="sxs-lookup"><span data-stu-id="93fc1-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="93fc1-142">Aby zmienić te ustawienia domyślne, należy dodać następujący kod XML do pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="93fc1-142">To change these defaults add the following XML to your App.config file.</span></span>

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a><span data-ttu-id="93fc1-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93fc1-143">See Also</span></span>

- [<span data-ttu-id="93fc1-144">Architektura aktywacji WAS</span><span class="sxs-lookup"><span data-stu-id="93fc1-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="93fc1-145">Konfigurowanie usługi WAS do użycia z programem WCF</span><span class="sxs-lookup"><span data-stu-id="93fc1-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="93fc1-146">Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="93fc1-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="93fc1-147">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="93fc1-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
