---
ms.openlocfilehash: 57f68c10d5d1edc9b8deaca2f4fe7edda2dd69b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620397"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="73357-101">Obiekt System. ServiceModel. Web. WebServiceHost nie dodaje już domyślnego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="73357-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="73357-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="73357-102">Details</span></span>

<span data-ttu-id="73357-103"><xref:System.ServiceModel.Web.WebServiceHost>Obiekt nie dodaje już domyślnego punktu końcowego, jeśli jawny punkt końcowy został dodany przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73357-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73357-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="73357-104">Suggestion</span></span>

<span data-ttu-id="73357-105">Jeśli użytkownicy będą mogli połączyć się z domyślnym punktem końcowym, a inne jawne punkty końcowe zostały dodane do <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> , domyślne punkty końcowe należy również dodać jawnie (przy użyciu <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="73357-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="73357-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="73357-106">Name</span></span>    | <span data-ttu-id="73357-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="73357-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73357-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="73357-108">Scope</span></span>   |<span data-ttu-id="73357-109">Mały</span><span class="sxs-lookup"><span data-stu-id="73357-109">Minor</span></span>|
|<span data-ttu-id="73357-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="73357-110">Version</span></span>|<span data-ttu-id="73357-111">4.5</span><span class="sxs-lookup"><span data-stu-id="73357-111">4.5</span></span>|
|<span data-ttu-id="73357-112">Typ</span><span class="sxs-lookup"><span data-stu-id="73357-112">Type</span></span>|<span data-ttu-id="73357-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="73357-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73357-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="73357-114">Affected APIs</span></span>

-<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li></ul>|
