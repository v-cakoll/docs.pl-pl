---
title: <configuration>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921249"
---
# <a name="configuration-element"></a><span data-ttu-id="b8369-102">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b8369-102">\<configuration> element</span></span>

<span data-ttu-id="b8369-103">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8369-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="b8369-104">**\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="b8369-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b8369-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8369-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="b8369-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8369-106">Attributes</span></span>

<span data-ttu-id="b8369-107">Brak</span><span class="sxs-lookup"><span data-stu-id="b8369-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="b8369-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="b8369-108">Parent element</span></span>

<span data-ttu-id="b8369-109">Brak</span><span class="sxs-lookup"><span data-stu-id="b8369-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="b8369-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8369-110">Child elements</span></span>

|     | <span data-ttu-id="b8369-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b8369-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b8369-112"> **\<> zestawubinding**</span><span class="sxs-lookup"><span data-stu-id="b8369-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="b8369-113">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8369-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="b8369-114">Schemat ustawień > uruchamiania  **\<** </span><span class="sxs-lookup"><span data-stu-id="b8369-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="b8369-115">Wszystkie elementy w schemacie ustawienia uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="b8369-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="b8369-116">Schemat ustawień **> środowiska uruchomieniowego \<** </span><span class="sxs-lookup"><span data-stu-id="b8369-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="b8369-117">Wszystkie elementy w schemacie ustawień środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b8369-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="b8369-118">[Schemat ustawień **> System. Runtime. Komunikacja zdalna \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8369-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="b8369-119">Wszystkie elementy w schemacie ustawień usług zdalnych.</span><span class="sxs-lookup"><span data-stu-id="b8369-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="b8369-120">Schemat ustawień **systemu .net > \<** </span><span class="sxs-lookup"><span data-stu-id="b8369-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="b8369-121">Wszystkie elementy w schemacie ustawień sieciowych.</span><span class="sxs-lookup"><span data-stu-id="b8369-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="b8369-122">Schemat ustawień > cryptographySettings  **\<** </span><span class="sxs-lookup"><span data-stu-id="b8369-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="b8369-123">Wszystkie elementy w schemacie ustawień kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="b8369-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="b8369-124">Schemat sekcji konfiguracji >  **\<** </span><span class="sxs-lookup"><span data-stu-id="b8369-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="b8369-125">Wszystkie elementy w schemacie ustawień sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8369-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="b8369-126">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="b8369-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="b8369-127">Wszystkie elementy w schemacie ustawienia śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="b8369-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="b8369-128">[Schemat ustawień konfiguracji ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8369-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="b8369-129">Wszystkie elementy w schemacie konfiguracji ASP.NET, w tym elementy służące do konfigurowania witryn i aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b8369-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="b8369-130">Używany w plikach *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="b8369-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="b8369-131">[Schemat ustawień > usług WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8369-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="b8369-132">Wszystkie elementy w schemacie ustawień usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b8369-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="b8369-133">Schemat ustawień internetowych</span><span class="sxs-lookup"><span data-stu-id="b8369-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="b8369-134">Wszystkie elementy w schemacie ustawień sieci Web, w tym elementy służące do konfigurowania sposobu działania programu ASP.NET z aplikacją hosta, taką jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="b8369-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="b8369-135">Używany w plikach *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="b8369-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b8369-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8369-136">Remarks</span></span>

<span data-ttu-id="b8369-137">Każdy plik konfiguracyjny musi zawierać dokładnie jeden  **\<element konfiguracji >** .</span><span class="sxs-lookup"><span data-stu-id="b8369-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8369-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8369-138">See also</span></span>

- [<span data-ttu-id="b8369-139">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8369-139">Configuration file schema for the .NET Framework</span></span>](index.md)
