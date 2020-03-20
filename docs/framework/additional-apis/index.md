---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155911"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="180c1-102">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="180c1-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="180c1-103">.NET Framework stale ewoluuje.</span><span class="sxs-lookup"><span data-stu-id="180c1-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="180c1-104">Aby poprawić rozwój między platformami i wprowadzić nowe funkcje wcześnie, nowe funkcje są wydawane poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="180c1-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="180c1-105">W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.</span><span class="sxs-lookup"><span data-stu-id="180c1-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="180c1-106">Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="180c1-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="180c1-107">Na przykład <xref:System.Text.CodePagesEncodingProvider> klasa udostępnia kodowanie stron kodowych aplikacjom platformy uniwersalnej systemu Windows opracowanym przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="180c1-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="180c1-108">W tym temacie wymieniono również te biblioteki.</span><span class="sxs-lookup"><span data-stu-id="180c1-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="180c1-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="180c1-109">OOB projects</span></span>
  
| <span data-ttu-id="180c1-110">Project</span><span class="sxs-lookup"><span data-stu-id="180c1-110">Project</span></span> | <span data-ttu-id="180c1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="180c1-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="180c1-112">Udostępnia kolekcje, które są bezpieczne dla wątków i gwarantuje, że nigdy nie zmienią ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="180c1-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="180c1-113">Udostępnia program obsługi <xref:System.Net.Http.HttpClient> wiadomości oparty na interfejsie WinHTTP systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="180c1-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="180c1-114">Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego simd.</span><span class="sxs-lookup"><span data-stu-id="180c1-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="180c1-115">Biblioteka przepływ danych TPL udostępnia składniki przepływu danych, aby zwiększyć niezawodność aplikacji obsługujących współbieżność.</span><span class="sxs-lookup"><span data-stu-id="180c1-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="180c1-116">Biblioteki specyficzne dla platformy</span><span class="sxs-lookup"><span data-stu-id="180c1-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="180c1-117">Project</span><span class="sxs-lookup"><span data-stu-id="180c1-117">Project</span></span> | <span data-ttu-id="180c1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="180c1-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="180c1-119">Rozszerza klasę, <xref:System.Text.EncodingProvider> aby kodowanie stron kodowych było dostępne dla aplikacji docelowych na platformie uniwersalnej systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="180c1-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="180c1-120">Prywatne interfejsy API</span><span class="sxs-lookup"><span data-stu-id="180c1-120">Private APIs</span></span>  

<span data-ttu-id="180c1-121">Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone/obsługiwane do użycia bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="180c1-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="180c1-122">Właściwość Microsoft.SqlServer.Server.SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="180c1-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="180c1-123">Metoda system.exception.prepForRemoting</span><span class="sxs-lookup"><span data-stu-id="180c1-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="180c1-124">Właściwość System.Data.SqlTypes.SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="180c1-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="180c1-125">System.Data.SqlTypes.SqlStreamChars Konstruktor</span><span class="sxs-lookup"><span data-stu-id="180c1-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="180c1-126">Właściwość System.Data.SqlTypes.SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="180c1-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="180c1-127">Właściwość System.Data.SqlTypes.SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="180c1-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="180c1-128">Właściwość System.Data.SqlTypes.SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="180c1-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="180c1-129">Metoda System.Data.SqlTypes.SqlStreamChars.Close</span><span class="sxs-lookup"><span data-stu-id="180c1-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="180c1-130">Metoda System.Data.SqlTypes.SqlStreamChars.Dispose</span><span class="sxs-lookup"><span data-stu-id="180c1-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="180c1-131">Metoda system.data.sqltypes.sqlstreamchars.flush</span><span class="sxs-lookup"><span data-stu-id="180c1-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="180c1-132">Metoda System.Data.SqlTypes.SqlStreamChars.Read</span><span class="sxs-lookup"><span data-stu-id="180c1-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="180c1-133">Metoda System.Data.SqlTypes.SqlStreamChars.Seek</span><span class="sxs-lookup"><span data-stu-id="180c1-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="180c1-134">Metoda System.Data.SqlTypes.SqlStreamChars.SetLength</span><span class="sxs-lookup"><span data-stu-id="180c1-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="180c1-135">Metoda System.Data.SqlTypes.SqlStreamChars.Write</span><span class="sxs-lookup"><span data-stu-id="180c1-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="180c1-136">Metoda System.IO.MemoryStream.InternalGetOriginAndLength</span><span class="sxs-lookup"><span data-stu-id="180c1-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="180c1-137">Klasa połączenia system.net.connection</span><span class="sxs-lookup"><span data-stu-id="180c1-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="180c1-138">Pole Lista zapisów\_system.net.connection.m</span><span class="sxs-lookup"><span data-stu-id="180c1-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="180c1-139">Klasa Grupy System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="180c1-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="180c1-140">Pole Lista połączeń system.Net.ConnectionGroup.m\_</span><span class="sxs-lookup"><span data-stu-id="180c1-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="180c1-141">Właściwość System.Net.ConnectStream.Connection</span><span class="sxs-lookup"><span data-stu-id="180c1-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="180c1-142">Klasa System.Net.CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="180c1-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="180c1-143">Pole Odpowiedzi System.Net.CoreResponseData.m\_</span><span class="sxs-lookup"><span data-stu-id="180c1-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="180c1-144">Pole Kod stanu System.Net.CoreResponseData.m\_</span><span class="sxs-lookup"><span data-stu-id="180c1-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="180c1-145">System.net.httpWebRequest. \_Pole Autoredirects</span><span class="sxs-lookup"><span data-stu-id="180c1-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="180c1-146">System.net.httpWebRequest. \_Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="180c1-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="180c1-147">System.net.httpWebRequest. \_Pole httpResponse</span><span class="sxs-lookup"><span data-stu-id="180c1-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="180c1-148">Właściwość System.Net.PooledStream.NetworkStream</span><span class="sxs-lookup"><span data-stu-id="180c1-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="180c1-149">Klasa System.Net.RtcState</span><span class="sxs-lookup"><span data-stu-id="180c1-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="180c1-150">Pole Lista połączeń system.Net.ServicePoint.m\_</span><span class="sxs-lookup"><span data-stu-id="180c1-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="180c1-151">Pole ServicePointTable w pliku\_System.Net.ServicePointManager.s</span><span class="sxs-lookup"><span data-stu-id="180c1-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="180c1-152">Pole system.net.TlsStream.m_Worker</span><span class="sxs-lookup"><span data-stu-id="180c1-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="180c1-153">Właściwość System.Net.Security.SslState.SslProtocol</span><span class="sxs-lookup"><span data-stu-id="180c1-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="180c1-154">Metoda System.ServiceModel.Channels.Message.BodyToString</span><span class="sxs-lookup"><span data-stu-id="180c1-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="180c1-155">System.ServiceModel.Channels.Message.WriteStartHeaders Metoda</span><span class="sxs-lookup"><span data-stu-id="180c1-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="180c1-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="180c1-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="180c1-157">Klasa System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="180c1-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="180c1-158">Klasa System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="180c1-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="180c1-159">Metoda system.Xml.XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="180c1-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="180c1-160">Adodb. Interfejs połączenia</span><span class="sxs-lookup"><span data-stu-id="180c1-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="180c1-161">Adodb. Wyliczenie eventreason</span><span class="sxs-lookup"><span data-stu-id="180c1-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="180c1-162">Adodb. Wyliczenie Statusu Zdarzeń</span><span class="sxs-lookup"><span data-stu-id="180c1-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="180c1-163">stdole. Struktura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="180c1-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="180c1-164">stdole. Struktura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="180c1-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="180c1-165">stdole. IFont.Name właściwość</span><span class="sxs-lookup"><span data-stu-id="180c1-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="180c1-166">stdole. Interfejs IFontDisp</span><span class="sxs-lookup"><span data-stu-id="180c1-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="180c1-167">stdole. Właściwość IPicture.Handle</span><span class="sxs-lookup"><span data-stu-id="180c1-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="180c1-168">stdole. Właściwość IPictureDisp.Handle</span><span class="sxs-lookup"><span data-stu-id="180c1-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="180c1-169">stdole. Interfejs StdFont</span><span class="sxs-lookup"><span data-stu-id="180c1-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="180c1-170">stdole. Interfejs stdPicture</span><span class="sxs-lookup"><span data-stu-id="180c1-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="180c1-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="180c1-171">See also</span></span>

* [<span data-ttu-id="180c1-172">Program .NET Framework i wydania poza harmonogramem (OOB)</span><span class="sxs-lookup"><span data-stu-id="180c1-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
