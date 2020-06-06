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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921249"
---
# <a name="configuration-element"></a><span data-ttu-id="9a963-102">\<configuration>, element</span><span class="sxs-lookup"><span data-stu-id="9a963-102">\<configuration> element</span></span>

<span data-ttu-id="9a963-103">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a963-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="9a963-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a963-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="9a963-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9a963-105">Attributes</span></span>

<span data-ttu-id="9a963-106">Brak</span><span class="sxs-lookup"><span data-stu-id="9a963-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9a963-107">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="9a963-107">Parent element</span></span>

<span data-ttu-id="9a963-108">Brak</span><span class="sxs-lookup"><span data-stu-id="9a963-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="9a963-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9a963-109">Child elements</span></span>

|     | <span data-ttu-id="9a963-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9a963-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="9a963-111">Określa zasady powiązań zestawów na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9a963-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="9a963-112">**\<startup>** Schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="9a963-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="9a963-113">Wszystkie elementy w schemacie ustawienia uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="9a963-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="9a963-114">**\<runtime>** Schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="9a963-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="9a963-115">Wszystkie elementy w schemacie ustawień środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9a963-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="9a963-116">[**\<system.runtime.remoting>** Schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a963-116">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="9a963-117">Wszystkie elementy w schemacie ustawień usług zdalnych.</span><span class="sxs-lookup"><span data-stu-id="9a963-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="9a963-118">**\<system.Net>** Schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="9a963-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="9a963-119">Wszystkie elementy w schemacie ustawień sieciowych.</span><span class="sxs-lookup"><span data-stu-id="9a963-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="9a963-120">**\<cryptographySettings>** Schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="9a963-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="9a963-121">Wszystkie elementy w schemacie ustawień kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="9a963-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="9a963-122">**\<configuration>** Schemat sekcji</span><span class="sxs-lookup"><span data-stu-id="9a963-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="9a963-123">Wszystkie elementy w schemacie ustawień sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9a963-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="9a963-124">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9a963-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="9a963-125">Wszystkie elementy w schemacie ustawienia śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="9a963-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="9a963-126">[Schemat ustawień konfiguracji ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a963-126">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="9a963-127">Wszystkie elementy w schemacie konfiguracji ASP.NET, w tym elementy służące do konfigurowania witryn i aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9a963-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="9a963-128">Używany w plikach *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="9a963-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="9a963-129">[**\<webServices>** Schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a963-129">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="9a963-130">Wszystkie elementy w schemacie ustawień usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9a963-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="9a963-131">Schemat ustawień sieci Web</span><span class="sxs-lookup"><span data-stu-id="9a963-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="9a963-132">Wszystkie elementy w schemacie ustawień sieci Web, w tym elementy służące do konfigurowania sposobu działania programu ASP.NET z aplikacją hosta, taką jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="9a963-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="9a963-133">Używany w plikach *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="9a963-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9a963-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a963-134">Remarks</span></span>

<span data-ttu-id="9a963-135">Każdy plik konfiguracji musi zawierać dokładnie jeden **\<configuration>** element.</span><span class="sxs-lookup"><span data-stu-id="9a963-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a963-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a963-136">See also</span></span>

- [<span data-ttu-id="9a963-137">Schemat pliku konfiguracji dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a963-137">Configuration file schema for the .NET Framework</span></span>](index.md)
