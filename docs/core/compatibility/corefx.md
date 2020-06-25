---
title: Podstawowe zmiany w bibliotece klas podstawowych
description: Wyświetla istotne zmiany w podstawowych bibliotekach programu .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365622"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="6e9de-103">Podstawowe zmiany w bibliotekach .NET</span><span class="sxs-lookup"><span data-stu-id="6e9de-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="6e9de-104">Podstawowe biblioteki .NET zapewniają pierwotne i inne typy ogólne używane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e9de-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="6e9de-105">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="6e9de-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6e9de-106">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="6e9de-106">Breaking change</span></span> | <span data-ttu-id="6e9de-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6e9de-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6e9de-108">Metody SSE i SSE2 CompareGreaterThan prawidłowo obsługują dane wejściowe NaN</span><span class="sxs-lookup"><span data-stu-id="6e9de-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="6e9de-109">5.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-109">5.0</span></span> |
| [<span data-ttu-id="6e9de-110">Element CounterSet. CreateCounterSetInstance teraz zgłasza InvalidOperationException, jeśli wystąpienie już istnieje</span><span class="sxs-lookup"><span data-stu-id="6e9de-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="6e9de-111">5.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-111">5.0</span></span> |
| [<span data-ttu-id="6e9de-112">Usunięto pakiet Microsoft. DotNet. PlatformAbstractions</span><span class="sxs-lookup"><span data-stu-id="6e9de-112">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="6e9de-113">5.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-113">5.0</span></span> |
| [<span data-ttu-id="6e9de-114">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="6e9de-114">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="6e9de-115">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-115">3.0</span></span> |
| [<span data-ttu-id="6e9de-116">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="6e9de-116">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="6e9de-117">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-117">3.0</span></span> |
| [<span data-ttu-id="6e9de-118">Zmiany zachowań formatowania zmiennoprzecinkowego i analizowania</span><span class="sxs-lookup"><span data-stu-id="6e9de-118">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="6e9de-119">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-119">3.0</span></span> |
| [<span data-ttu-id="6e9de-120">Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow</span><span class="sxs-lookup"><span data-stu-id="6e9de-120">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="6e9de-121">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-121">3.0</span></span> |
| [<span data-ttu-id="6e9de-122">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="6e9de-122">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="6e9de-123">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-123">3.0</span></span> |
| [<span data-ttu-id="6e9de-124">Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="6e9de-124">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="6e9de-125">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-125">3.0</span></span> |
| [<span data-ttu-id="6e9de-126">TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="6e9de-126">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="6e9de-127">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-127">3.0</span></span> |
| [<span data-ttu-id="6e9de-128">Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów</span><span class="sxs-lookup"><span data-stu-id="6e9de-128">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="6e9de-129">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-129">3.0</span></span> |
| [<span data-ttu-id="6e9de-130">Typ wyjątku serializatora JSON został zmieniony z elementu Jsonexception na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="6e9de-130">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="6e9de-131">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-131">3.0</span></span> |
| [<span data-ttu-id="6e9de-132">Zmień semantykę (String) na wartość null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="6e9de-132">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="6e9de-133">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-133">3.0</span></span> |
| [<span data-ttu-id="6e9de-134">Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="6e9de-134">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="6e9de-135">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-135">3.0</span></span> |
| [<span data-ttu-id="6e9de-136">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="6e9de-136">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="6e9de-137">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-137">3.0</span></span> |
| [<span data-ttu-id="6e9de-138">Zmiany interfejsu API jsonelement</span><span class="sxs-lookup"><span data-stu-id="6e9de-138">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="6e9de-139">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-139">3.0</span></span> |
| [<span data-ttu-id="6e9de-140">Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init</span><span class="sxs-lookup"><span data-stu-id="6e9de-140">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="6e9de-141">3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-141">3.0</span></span> |
| [<span data-ttu-id="6e9de-142">Pola prywatne dodane do wbudowanych typów struktur</span><span class="sxs-lookup"><span data-stu-id="6e9de-142">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="6e9de-143">2.1</span><span class="sxs-lookup"><span data-stu-id="6e9de-143">2.1</span></span> |
| [<span data-ttu-id="6e9de-144">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="6e9de-144">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="6e9de-145">2.1</span><span class="sxs-lookup"><span data-stu-id="6e9de-145">2.1</span></span> |
| [<span data-ttu-id="6e9de-146">Wersje OpenSSL na macOS</span><span class="sxs-lookup"><span data-stu-id="6e9de-146">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="6e9de-147">2.1</span><span class="sxs-lookup"><span data-stu-id="6e9de-147">2.1</span></span> |
| [<span data-ttu-id="6e9de-148">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="6e9de-148">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="6e9de-149">1.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-149">1.0</span></span> |
| [<span data-ttu-id="6e9de-150">Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="6e9de-150">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="6e9de-151">1.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-151">1.0</span></span> |
| [<span data-ttu-id="6e9de-152">Właściwości UriBuilder nie dołączają już znaków wiodących</span><span class="sxs-lookup"><span data-stu-id="6e9de-152">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="6e9de-153">1.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-153">1.0</span></span> |
| [<span data-ttu-id="6e9de-154">Proces. element StartInfo zgłasza InvalidOperationException dla procesów, które nie zostały uruchomione</span><span class="sxs-lookup"><span data-stu-id="6e9de-154">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="6e9de-155">1.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-155">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6e9de-156">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6e9de-156">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="6e9de-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6e9de-157">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="6e9de-158">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6e9de-158">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="6e9de-159">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6e9de-159">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
