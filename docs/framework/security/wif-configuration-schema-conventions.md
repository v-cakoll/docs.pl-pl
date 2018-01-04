---
title: Konwencje schematu konfiguracji WIF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="db707-102">Konwencje schematu konfiguracji WIF</span><span class="sxs-lookup"><span data-stu-id="db707-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="db707-103">W tym temacie opisano konwencje używanych w całym tematy dotyczące konfiguracji systemu Windows Identity Foundation (WIF) oraz opisano niektóre typowe funkcje i atrybuty stosowane w [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sekcje.</span><span class="sxs-lookup"><span data-stu-id="db707-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="db707-104">Tryby</span><span class="sxs-lookup"><span data-stu-id="db707-104">Modes</span></span>  
 <span data-ttu-id="db707-105">Wiele elementów konfiguracji programu WIF `mode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="db707-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="db707-106">Ten atrybut kontroluje zwykle, których klasa jest używana do określonej części przetwarzania i elementy konfiguracji, które są dozwolone jako elementy podrzędne bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="db707-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="db707-107">Błąd konfiguracji zostanie wygenerowany, jeśli elementy, które znajdują się w pliku konfiguracji są ignorowane z powodu ustawienia trybu.</span><span class="sxs-lookup"><span data-stu-id="db707-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="db707-108">Wartości TimeSpan</span><span class="sxs-lookup"><span data-stu-id="db707-108">Timespan Values</span></span>  
 <span data-ttu-id="db707-109">Gdzie <xref:System.TimeSpan> jest używany jako typ atrybutu, zobacz <xref:System.TimeSpan.Parse%28System.String%29> metody, aby zobaczyć dozwolone formatu.</span><span class="sxs-lookup"><span data-stu-id="db707-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="db707-110">Ten format jest zgodny ze specyfikacją następujące.</span><span class="sxs-lookup"><span data-stu-id="db707-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="db707-111">Na przykład "30", "30.00:00", "30.00:00:00" wszystkie oznacza 30 dni; i "00:05", "00: 05:00", "0.00:05:00.00" oznacza wszystkie 5 minut.</span><span class="sxs-lookup"><span data-stu-id="db707-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="db707-112">Odwołania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="db707-112">Certificate References</span></span>  
 <span data-ttu-id="db707-113">Odwołania do certyfikatów przy użyciu podjąć kilka elementów `<certificateReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="db707-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="db707-114">Podczas odwoływania się do certyfikatu, następujące atrybuty są dostępne.</span><span class="sxs-lookup"><span data-stu-id="db707-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="db707-115">Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wyliczenie: `CurrentUser` lub `CurrentMachine`.</span><span class="sxs-lookup"><span data-stu-id="db707-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="db707-116">Wartość <xref:System.Security.Cryptography.X509Certificates.StoreName> wyliczenie; najbardziej przydatne dla tego kontekstu są `My` i `TrustedPeople`.</span><span class="sxs-lookup"><span data-stu-id="db707-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="db707-117">Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> wyliczenie; najbardziej przydatne dla tego kontekstu są `FindBySubjectName` i `FindByThumbprint`.</span><span class="sxs-lookup"><span data-stu-id="db707-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="db707-118">Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="db707-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="db707-119">Wartość używana do znajdowania certyfikatu, na podstawie `x509FindType` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="db707-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="db707-120">Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="db707-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="db707-121">Gdy `FindByThumbPrint` jest określony, ten atrybut ma wartość, która jest formularz ciąg szesnastkowy certyfikatu odcisku palca, na przykład "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span><span class="sxs-lookup"><span data-stu-id="db707-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="db707-122">Odwołania do niestandardowego typu</span><span class="sxs-lookup"><span data-stu-id="db707-122">Custom Type References</span></span>  
 <span data-ttu-id="db707-123">Dokumentacja elementów kilka typów niestandardowych za pomocą `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="db707-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="db707-124">Ten atrybut powinien określać nazwę typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="db707-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="db707-125">Aby odwołać się do typu z globalnej pamięci podręcznej zestawów (GAC), można użyć silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="db707-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="db707-126">Aby odwołać się do typu z zestawu w pojemniku / directory, może służyć proste odwołanie kwalifikowaną dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="db707-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="db707-127">Typy definiowane w App_Code / katalogu mogą się też odwoływać linie po prostu określić nazwę typu z nie kwalifikującego zestawu.</span><span class="sxs-lookup"><span data-stu-id="db707-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="db707-128">Niestandardowe typy musi pochodzić od typu określonego i użytkownik musi podać `public` domyślnego konstruktora (0 argument).</span><span class="sxs-lookup"><span data-stu-id="db707-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db707-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db707-129">See Also</span></span>  
 [<span data-ttu-id="db707-130">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="db707-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="db707-131">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="db707-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
