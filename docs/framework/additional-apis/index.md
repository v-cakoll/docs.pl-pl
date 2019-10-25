---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 4b47847e9d6e9424d4442d655c40a637383c7229
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847078"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="23ea6-102">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="23ea6-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="23ea6-103">.NET Framework ciągle się zmienia.</span><span class="sxs-lookup"><span data-stu-id="23ea6-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="23ea6-104">Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, nowe funkcje są uwalniane poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="23ea6-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="23ea6-105">W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.</span><span class="sxs-lookup"><span data-stu-id="23ea6-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="23ea6-106">Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23ea6-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="23ea6-107">Na przykład Klasa <xref:System.Text.CodePagesEncodingProvider> sprawia, że kodowanie stron kodowych jest dostępne dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23ea6-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="23ea6-108">W tym temacie wymieniono również te biblioteki.</span><span class="sxs-lookup"><span data-stu-id="23ea6-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="23ea6-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="23ea6-109">OOB projects</span></span>
  
| <span data-ttu-id="23ea6-110">Projekt</span><span class="sxs-lookup"><span data-stu-id="23ea6-110">Project</span></span> | <span data-ttu-id="23ea6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="23ea6-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="23ea6-112">Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="23ea6-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="23ea6-113">Zapewnia obsługę komunikatów dla <xref:System.Net.Http.HttpClient> w oparciu o interfejs WinHTTP systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23ea6-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="23ea6-114">Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.</span><span class="sxs-lookup"><span data-stu-id="23ea6-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="23ea6-115">Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności.</span><span class="sxs-lookup"><span data-stu-id="23ea6-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="23ea6-116">Biblioteki specyficzne dla platformy</span><span class="sxs-lookup"><span data-stu-id="23ea6-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="23ea6-117">Projekt</span><span class="sxs-lookup"><span data-stu-id="23ea6-117">Project</span></span> | <span data-ttu-id="23ea6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="23ea6-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="23ea6-119">Rozszerza klasę <xref:System.Text.EncodingProvider>, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23ea6-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="23ea6-120">Prywatne interfejsy API</span><span class="sxs-lookup"><span data-stu-id="23ea6-120">Private APIs</span></span>  

<span data-ttu-id="23ea6-121">Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="23ea6-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="23ea6-122">Microsoft. SqlServer. Server. SmiOrderProperty. Item — Właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="23ea6-123">System. Exception. PrepForRemoting — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="23ea6-124">System. Data. SqlTypes. SqlChars. Stream — Właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="23ea6-125">System. Data. SqlTypes. SqlStreamChars — Konstruktor</span><span class="sxs-lookup"><span data-stu-id="23ea6-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="23ea6-126">Właściwość system. Data. SqlTypes. SqlStreamChars. CanSeek</span><span class="sxs-lookup"><span data-stu-id="23ea6-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="23ea6-127">Właściwość system. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="23ea6-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="23ea6-128">System. Data. SqlTypes. SqlStreamChars. Length — właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="23ea6-129">System. Data. SqlTypes. SqlStreamChars. Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="23ea6-130">System. Data. SqlTypes. SqlStreamChars. Dispose — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="23ea6-131">System. Data. SqlTypes. SqlStreamChars. Flush — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="23ea6-132">System. Data. SqlTypes. SqlStreamChars. Read — metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="23ea6-133">System. Data. SqlTypes. SqlStreamChars. Seek — metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="23ea6-134">System. Data. SqlTypes. SqlStreamChars. SetLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="23ea6-135">System. Data. SqlTypes. SqlStreamChars. Write — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="23ea6-136">System .NET. Connection — Klasa</span><span class="sxs-lookup"><span data-stu-id="23ea6-136">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="23ea6-137">System .NET. Connection. m\_pole WriteList</span><span class="sxs-lookup"><span data-stu-id="23ea6-137">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="23ea6-138">System .NET. Connection — Klasa</span><span class="sxs-lookup"><span data-stu-id="23ea6-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="23ea6-139">System .NET. Connections. m\_pole ConnectionList</span><span class="sxs-lookup"><span data-stu-id="23ea6-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="23ea6-140">Właściwość system .NET. ConnectStream. Connection</span><span class="sxs-lookup"><span data-stu-id="23ea6-140">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="23ea6-141">System .NET. CoreResponseData, Klasa</span><span class="sxs-lookup"><span data-stu-id="23ea6-141">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="23ea6-142">Pole System .NET. CoreResponseData. m\_ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="23ea6-142">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="23ea6-143">System .NET. CoreResponseData. m\_pole StatusCode</span><span class="sxs-lookup"><span data-stu-id="23ea6-143">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="23ea6-144">Pole System .NET. HttpWebRequest.\_autoredirects</span><span class="sxs-lookup"><span data-stu-id="23ea6-144">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="23ea6-145">Pole System .NET. HttpWebRequest.\_CoreResponse</span><span class="sxs-lookup"><span data-stu-id="23ea6-145">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="23ea6-146">Pole System .NET. HttpWebRequest.\_HttpResponse</span><span class="sxs-lookup"><span data-stu-id="23ea6-146">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="23ea6-147">System .NET. PooledStream. NetworkStream — Właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-147">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="23ea6-148">Pole System .NET. ServicePoint. m\_ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="23ea6-148">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="23ea6-149">System .NET. ServicePointManager. s\_pole ServicePoint</span><span class="sxs-lookup"><span data-stu-id="23ea6-149">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="23ea6-150">Pole System .NET. TlsStream. m_Worker</span><span class="sxs-lookup"><span data-stu-id="23ea6-150">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="23ea6-151">System .NET. Security. SslState. SslProtocol — Właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-151">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="23ea6-152">System. Windows. Diagnostics. VisualDiagnostics. s\_isDebuggerCheckDisabledForTestPurposes pole</span><span class="sxs-lookup"><span data-stu-id="23ea6-152">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="23ea6-153">System. Windows. Forms. Design. DataMemberFieldEditor — Klasa</span><span class="sxs-lookup"><span data-stu-id="23ea6-153">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="23ea6-154">System. Windows. Forms. Design. Datamemberfieldeditor — Klasa</span><span class="sxs-lookup"><span data-stu-id="23ea6-154">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="23ea6-155">System. XML. XmlReader. CreateSqlReader — Metoda</span><span class="sxs-lookup"><span data-stu-id="23ea6-155">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="23ea6-156">ADODB. Interfejs połączenia</span><span class="sxs-lookup"><span data-stu-id="23ea6-156">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="23ea6-157">ADODB. Wyliczenie EventReason</span><span class="sxs-lookup"><span data-stu-id="23ea6-157">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="23ea6-158">ADODB. Wyliczenie obiektu EventStatus</span><span class="sxs-lookup"><span data-stu-id="23ea6-158">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="23ea6-159">stdole. DISPPARAMS, struktura</span><span class="sxs-lookup"><span data-stu-id="23ea6-159">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="23ea6-160">stdole. EXCEPINFO, struktura</span><span class="sxs-lookup"><span data-stu-id="23ea6-160">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="23ea6-161">stdole. Właściwość IFont.Name</span><span class="sxs-lookup"><span data-stu-id="23ea6-161">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="23ea6-162">stdole. IFontDisp, interfejs</span><span class="sxs-lookup"><span data-stu-id="23ea6-162">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="23ea6-163">stdole. IPicture. Handle — właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-163">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="23ea6-164">stdole. IPictureDisp. Handle — właściwość</span><span class="sxs-lookup"><span data-stu-id="23ea6-164">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="23ea6-165">stdole. StdFont, interfejs</span><span class="sxs-lookup"><span data-stu-id="23ea6-165">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="23ea6-166">stdole. StdPicture, interfejs</span><span class="sxs-lookup"><span data-stu-id="23ea6-166">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="23ea6-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23ea6-167">See also</span></span>

* [<span data-ttu-id="23ea6-168">Program .NET Framework i wydania poza harmonogramem (OOB)</span><span class="sxs-lookup"><span data-stu-id="23ea6-168">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
