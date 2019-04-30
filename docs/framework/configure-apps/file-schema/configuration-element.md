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
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705418"
---
# <a name="configuration-element"></a><span data-ttu-id="3a319-102">\<Konfiguracja > element</span><span class="sxs-lookup"><span data-stu-id="3a319-102">\<configuration> element</span></span>

<span data-ttu-id="3a319-103">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a319-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="3a319-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="3a319-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3a319-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a319-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="3a319-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a319-106">Attributes</span></span>

<span data-ttu-id="3a319-107">Brak</span><span class="sxs-lookup"><span data-stu-id="3a319-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3a319-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="3a319-108">Parent element</span></span>

<span data-ttu-id="3a319-109">Brak</span><span class="sxs-lookup"><span data-stu-id="3a319-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="3a319-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a319-110">Child elements</span></span>

|     | <span data-ttu-id="3a319-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3a319-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3a319-112">**\<assemblybinding — >**</span><span class="sxs-lookup"><span data-stu-id="3a319-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="3a319-113">Określa politykę powiązania zestawu na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a319-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="3a319-114">**\<Uruchamianie >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="3a319-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="3a319-115">Wszystkie elementy w schemacie ustawień uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="3a319-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="3a319-116">**\<środowisko uruchomieniowe >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="3a319-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="3a319-117">Wszystkie elementy w schemacie ustawień środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3a319-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="3a319-118">[**\<System.Runtime.Remoting >** schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3a319-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="3a319-119">Wszystkie elementy w schemacie ustawień komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="3a319-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="3a319-120">**\<system.Net>** Settings Schema</span><span class="sxs-lookup"><span data-stu-id="3a319-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="3a319-121">Wszystkie elementy w schemacie ustawień sieci.</span><span class="sxs-lookup"><span data-stu-id="3a319-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="3a319-122">**\<cryptographySettings>** Settings Schema</span><span class="sxs-lookup"><span data-stu-id="3a319-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="3a319-123">Wszystkie elementy w schemacie ustawień kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="3a319-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="3a319-124">**\<Konfiguracja >** schemat sekcji</span><span class="sxs-lookup"><span data-stu-id="3a319-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="3a319-125">Wszystkie elementy w schemacie ustawień sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a319-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="3a319-126">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="3a319-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="3a319-127">Wszystkie elementy w schemacie ustawień śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="3a319-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="3a319-128">[Schemat ustawień konfiguracji programu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3a319-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="3a319-129">Wszystkie elementy w schemacie konfiguracji platformy ASP.NET, które zawierają elementy umożliwiające konfigurację witryn sieci Web platformy ASP.NET i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a319-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="3a319-130">Używane w *Web.config* plików.</span><span class="sxs-lookup"><span data-stu-id="3a319-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="3a319-131">[**\<usługi sieci Web >** schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3a319-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="3a319-132">Wszystkie elementy w schemacie ustawień usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3a319-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="3a319-133">Schemat ustawień internetowych</span><span class="sxs-lookup"><span data-stu-id="3a319-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="3a319-134">Wszystkie elementy w schemacie ustawień sieci Web zawierają elementy umożliwiające konfigurację działania programu ASP.NET z aplikacją hosta, takich jak usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="3a319-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="3a319-135">Używane w *aspnet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="3a319-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3a319-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a319-136">Remarks</span></span>

<span data-ttu-id="3a319-137">Każdy plik konfiguracji musi zawierać dokładnie jeden  **\<konfiguracji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="3a319-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a319-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a319-138">See also</span></span>

- [<span data-ttu-id="3a319-139">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3a319-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
