---
title: Dodatkowe biblioteki klas i interfejsy API
description: Poznaj dodatkowe biblioteki klas i interfejsy API w programie .NET, w tym projekty poza pasmem (OOB), biblioteki specyficzne dla platformy i prywatne interfejsy API.
ms.date: 06/12/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 0b888d2f0e80685ba993682b2f3067cf8aee15bc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989739"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="64ed9-103">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="64ed9-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="64ed9-104">Ten artykuł zawiera listę .NET Framework interfejsów API, które zostały wydane poza pasmem, przeznaczone dla konkretnej platformy lub są typami prywatnymi lub wewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="64ed9-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="64ed9-105">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="64ed9-105">OOB projects</span></span>

<span data-ttu-id="64ed9-106">Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, niektóre .NET Framework funkcje zostały wydane poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="64ed9-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="64ed9-107">Project</span><span class="sxs-lookup"><span data-stu-id="64ed9-107">Project</span></span> | <span data-ttu-id="64ed9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="64ed9-108">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="64ed9-109">Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="64ed9-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="64ed9-110">Zapewnia obsługę komunikatów dla programu na <xref:System.Net.Http.HttpClient> podstawie interfejsu WinHTTP systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64ed9-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="64ed9-111">Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.</span><span class="sxs-lookup"><span data-stu-id="64ed9-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="64ed9-112">Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności.</span><span class="sxs-lookup"><span data-stu-id="64ed9-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="64ed9-113">Biblioteki specyficzne dla platformy</span><span class="sxs-lookup"><span data-stu-id="64ed9-113">Platform-specific libraries</span></span>

<span data-ttu-id="64ed9-114">Niektóre biblioteki są przeznaczone dla konkretnych platform.</span><span class="sxs-lookup"><span data-stu-id="64ed9-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="64ed9-115">Na przykład <xref:System.Text.CodePagesEncodingProvider> Klasa udostępnia kodowanie stron kodowych dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="64ed9-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>
  
| <span data-ttu-id="64ed9-116">Project</span><span class="sxs-lookup"><span data-stu-id="64ed9-116">Project</span></span> | <span data-ttu-id="64ed9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="64ed9-117">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="64ed9-118">Rozszerza <xref:System.Text.EncodingProvider> klasę, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64ed9-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="64ed9-119">Prywatne interfejsy API</span><span class="sxs-lookup"><span data-stu-id="64ed9-119">Private APIs</span></span>  

<span data-ttu-id="64ed9-120">Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="64ed9-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="64ed9-121">Microsoft. SqlServer. Server. SmiOrderProperty. Item — Właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="64ed9-122">System. Exception. PrepForRemoting — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="64ed9-123">System. Data. SqlTypes. SqlChars. Stream — Właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="64ed9-124">System. Data. SqlTypes. SqlStreamChars — Konstruktor</span><span class="sxs-lookup"><span data-stu-id="64ed9-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="64ed9-125">Właściwość system. Data. SqlTypes. SqlStreamChars. CanSeek</span><span class="sxs-lookup"><span data-stu-id="64ed9-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="64ed9-126">Właściwość system. Data. SqlTypes. SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="64ed9-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="64ed9-127">System. Data. SqlTypes. SqlStreamChars. Length — właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="64ed9-128">System. Data. SqlTypes. SqlStreamChars. Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="64ed9-129">System. Data. SqlTypes. SqlStreamChars. Dispose — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="64ed9-130">System. Data. SqlTypes. SqlStreamChars. Flush — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="64ed9-131">System. Data. SqlTypes. SqlStreamChars. Read — metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="64ed9-132">System. Data. SqlTypes. SqlStreamChars. Seek — metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="64ed9-133">System. Data. SqlTypes. SqlStreamChars. SetLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="64ed9-134">System. Data. SqlTypes. SqlStreamChars. Write — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="64ed9-135">System. IO. elementu MemoryStream. InternalGetOriginAndLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="64ed9-136">System .NET. ComNetOS, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="64ed9-137">System .NET. Connection — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="64ed9-138">Pole System .NET. Connection. m \_ WriteList</span><span class="sxs-lookup"><span data-stu-id="64ed9-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="64ed9-139">System .NET. Connection — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="64ed9-140">Pole System .NET. Connections. m \_ ConnectionList</span><span class="sxs-lookup"><span data-stu-id="64ed9-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="64ed9-141">Właściwość system .NET. ConnectStream. Connection</span><span class="sxs-lookup"><span data-stu-id="64ed9-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="64ed9-142">System .NET. CoreResponseData, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="64ed9-143">Pole System .NET. CoreResponseData. m \_ ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="64ed9-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="64ed9-144">Pole StatusCode systemu .NET. CoreResponseData. m \_</span><span class="sxs-lookup"><span data-stu-id="64ed9-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="64ed9-145">System .NET. ExceptionHelper, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="64ed9-146">System .NET. HttpStatusDescription, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="64ed9-147">System .NET. HttpWebRequest. \_ Pole autoredirect</span><span class="sxs-lookup"><span data-stu-id="64ed9-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="64ed9-148">System .NET. HttpWebRequest. \_ Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="64ed9-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="64ed9-149">System .NET. HttpWebRequest. \_ Pole HttpResponse</span><span class="sxs-lookup"><span data-stu-id="64ed9-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="64ed9-150">System .NET. Logging — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="64ed9-151">System .NET. mail. MailAddressParser — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="64ed9-152">System .NET. mail. QuotedPairReader — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="64ed9-153">System .NET. MIME. MailBnfHelper — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="64ed9-154">System .NET. PooledStream. NetworkStream — Właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="64ed9-155">System .NET. RtcState, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="64ed9-156">System .NET. Security. SslState. SslProtocol — Właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="64ed9-157">Pole System .NET. ServicePoint. m \_ ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="64ed9-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="64ed9-158">System .NET. ServicePointManager. CloseConnectionGroups — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="64ed9-159">System .NET. ServicePointManager. s — \_ pole ServicePoint</span><span class="sxs-lookup"><span data-stu-id="64ed9-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="64ed9-160">Pole System .NET. TlsStream. m_Worker</span><span class="sxs-lookup"><span data-stu-id="64ed9-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="64ed9-161">System .NET. UnsafeNclNativeMethods, Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="64ed9-162">System .NET. WebHeaderCollection. addinternal — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="64ed9-163">System. ServiceModel. Channels. Message. BodyToString — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="64ed9-164">System. ServiceModel. Channels. Message. WriteStartHeaders — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="64ed9-165">Pole System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="64ed9-165">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="64ed9-166">System. Windows. Forms. Design. DataMemberFieldEditor — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-166">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="64ed9-167">System. Windows. Forms. Design. Datamemberfieldeditor — Klasa</span><span class="sxs-lookup"><span data-stu-id="64ed9-167">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="64ed9-168">System.Xml.XmlReader. CreateSqlReader — Metoda</span><span class="sxs-lookup"><span data-stu-id="64ed9-168">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="64ed9-169">ADODB. Interfejs połączenia</span><span class="sxs-lookup"><span data-stu-id="64ed9-169">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="64ed9-170">ADODB. Wyliczenie EventReason</span><span class="sxs-lookup"><span data-stu-id="64ed9-170">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="64ed9-171">ADODB. Wyliczenie obiektu EventStatus</span><span class="sxs-lookup"><span data-stu-id="64ed9-171">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="64ed9-172">stdole. DISPPARAMS, struktura</span><span class="sxs-lookup"><span data-stu-id="64ed9-172">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="64ed9-173">stdole. EXCEPINFO, struktura</span><span class="sxs-lookup"><span data-stu-id="64ed9-173">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="64ed9-174">stdole. Właściwość IFont.Name</span><span class="sxs-lookup"><span data-stu-id="64ed9-174">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="64ed9-175">stdole. IFontDisp, interfejs</span><span class="sxs-lookup"><span data-stu-id="64ed9-175">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="64ed9-176">stdole. IPicture. Handle — właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-176">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="64ed9-177">stdole. IPictureDisp. Handle — właściwość</span><span class="sxs-lookup"><span data-stu-id="64ed9-177">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="64ed9-178">stdole. StdFont, interfejs</span><span class="sxs-lookup"><span data-stu-id="64ed9-178">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="64ed9-179">stdole. StdPicture, interfejs</span><span class="sxs-lookup"><span data-stu-id="64ed9-179">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="64ed9-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64ed9-180">See also</span></span>

* [<span data-ttu-id="64ed9-181">.NET Framework i wersje poza pasmem</span><span class="sxs-lookup"><span data-stu-id="64ed9-181">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
