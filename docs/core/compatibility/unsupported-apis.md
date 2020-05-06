---
title: Nieobsługiwane interfejsy API w programie .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794601"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="e5e82-103">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5e82-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="e5e82-104">Następujące interfejsy API zawsze będą zgłaszać <xref:System.PlatformNotSupportedException> na platformie .NET Core na wszystkich lub podzestawach platform.</span><span class="sxs-lookup"><span data-stu-id="e5e82-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="e5e82-105">Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e82-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e5e82-106">Ten artykuł jest pracą w toku.</span><span class="sxs-lookup"><span data-stu-id="e5e82-106">This article is a work-in-progress.</span></span> <span data-ttu-id="e5e82-107">Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5e82-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="e5e82-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5e82-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="e5e82-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="e5e82-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="e5e82-110">System</span><span class="sxs-lookup"><span data-stu-id="e5e82-110">System</span></span>

| <span data-ttu-id="e5e82-111">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-111">Member</span></span> | <span data-ttu-id="e5e82-112">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-113">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-114">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="e5e82-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="e5e82-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-117">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="e5e82-118">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e5e82-119">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e5e82-120">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-121">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-122">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="e5e82-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="e5e82-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="e5e82-124">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-124">Member</span></span> | <span data-ttu-id="e5e82-125">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-126">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-127">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-128">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="e5e82-129">System. Collections. specjalizowane</span><span class="sxs-lookup"><span data-stu-id="e5e82-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="e5e82-130">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-130">Member</span></span> | <span data-ttu-id="e5e82-131">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-132">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-133">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-134">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="e5e82-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="e5e82-135">System.Configuration</span></span>

| <span data-ttu-id="e5e82-136">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-136">Member</span></span> | <span data-ttu-id="e5e82-137">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e5e82-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="e5e82-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="e5e82-139">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="e5e82-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="e5e82-140">System.Console</span></span>

| <span data-ttu-id="e5e82-141">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-141">Member</span></span> | <span data-ttu-id="e5e82-142">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="e5e82-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-143">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-145">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-147">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-149">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="e5e82-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e5e82-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-154">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-155"><xref:System.Console.Title?displayProperty=nameWithType>(tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="e5e82-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e5e82-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-156">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-158">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-160">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-162">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="e5e82-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="e5e82-165">System.Data.Common</span></span>

| <span data-ttu-id="e5e82-166">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-166">Member</span></span> | <span data-ttu-id="e5e82-167">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e5e82-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(zgłasza <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="e5e82-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="e5e82-169">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="e5e82-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="e5e82-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="e5e82-171">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-171">Member</span></span> | <span data-ttu-id="e5e82-172">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e5e82-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-174">Linux</span><span class="sxs-lookup"><span data-stu-id="e5e82-174">Linux</span></span> |
| <span data-ttu-id="e5e82-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-176">Linux</span><span class="sxs-lookup"><span data-stu-id="e5e82-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="e5e82-177">macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="e5e82-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="e5e82-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="e5e82-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="e5e82-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="e5e82-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-183">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-185">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="e5e82-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e5e82-187">macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-187">macOS</span></span> |
| <span data-ttu-id="e5e82-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="e5e82-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="e5e82-190">System.IO</span></span>

| <span data-ttu-id="e5e82-191">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-191">Member</span></span> | <span data-ttu-id="e5e82-192">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-193">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-194">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="e5e82-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="e5e82-195">System.IO.Pipes</span></span>

| <span data-ttu-id="e5e82-196">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-196">Member</span></span> | <span data-ttu-id="e5e82-197">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="e5e82-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="e5e82-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e5e82-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e5e82-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-201">Linux and macOS</span></span> |
| <span data-ttu-id="e5e82-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="e5e82-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="e5e82-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="e5e82-205">System.Media</span></span>

| <span data-ttu-id="e5e82-206">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-206">Member</span></span> | <span data-ttu-id="e5e82-207">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-208">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="e5e82-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="e5e82-209">System.Net</span></span>

| <span data-ttu-id="e5e82-210">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-210">Member</span></span> | <span data-ttu-id="e5e82-211">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-212">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-213">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-214">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-215">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-216">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-217">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-218">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-219">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-220">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-221">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-222">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="e5e82-223">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-224">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-225">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-226">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-227">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-228">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="e5e82-229">System .NET. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="e5e82-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="e5e82-230">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-230">Member</span></span> | <span data-ttu-id="e5e82-231">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-232">Windows (platformy UWP)</span><span class="sxs-lookup"><span data-stu-id="e5e82-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="e5e82-233">System .NET. Sockets</span><span class="sxs-lookup"><span data-stu-id="e5e82-233">System.Net.Sockets</span></span>

| <span data-ttu-id="e5e82-234">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-234">Member</span></span> | <span data-ttu-id="e5e82-235">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="e5e82-236">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-237">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="e5e82-238">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="e5e82-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="e5e82-239">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-239">Member</span></span> | <span data-ttu-id="e5e82-240">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="e5e82-241">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="e5e82-242">System. odbicie</span><span class="sxs-lookup"><span data-stu-id="e5e82-242">System.Reflection</span></span>

| <span data-ttu-id="e5e82-243">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-243">Member</span></span> | <span data-ttu-id="e5e82-244">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-245">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-246">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-247">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-248">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="e5e82-249">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-250">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="e5e82-251">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="e5e82-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="e5e82-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="e5e82-253">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-253">Member</span></span> | <span data-ttu-id="e5e82-254">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="e5e82-255">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="e5e82-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="e5e82-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="e5e82-257">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-257">Member</span></span> | <span data-ttu-id="e5e82-258">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-259">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="e5e82-260">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-261">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-262">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-265">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="e5e82-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="e5e82-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="e5e82-267">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-267">Member</span></span> | <span data-ttu-id="e5e82-268">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="e5e82-269">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="e5e82-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="e5e82-270">System.Security</span></span>

| <span data-ttu-id="e5e82-271">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-271">Member</span></span> | <span data-ttu-id="e5e82-272">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="e5e82-273">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e5e82-274">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-275">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="e5e82-276">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e5e82-277">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="e5e82-278">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="e5e82-279">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="e5e82-280">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e5e82-281">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e5e82-282">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="e5e82-283">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-284">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="e5e82-285">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="e5e82-286">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="e5e82-287">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="e5e82-287">System.Security.Claims</span></span>

| <span data-ttu-id="e5e82-288">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-288">Member</span></span> | <span data-ttu-id="e5e82-289">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="e5e82-290">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-291">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="e5e82-292">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-293">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-294">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="e5e82-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="e5e82-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="e5e82-296">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-296">Member</span></span> | <span data-ttu-id="e5e82-297">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-298">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="e5e82-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="e5e82-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="e5e82-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="e5e82-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e5e82-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="e5e82-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="e5e82-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="e5e82-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="e5e82-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="e5e82-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="e5e82-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="e5e82-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e5e82-311">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e5e82-312">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="e5e82-313">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-314">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-315">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-316">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-317">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e5e82-318">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-319">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="e5e82-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-322">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-323">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e5e82-324">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-325">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="e5e82-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="e5e82-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="e5e82-327">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-327">Member</span></span> | <span data-ttu-id="e5e82-328">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="e5e82-329">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-330">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="e5e82-331">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="e5e82-332">System. Security. Cryptography. x509</span><span class="sxs-lookup"><span data-stu-id="e5e82-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="e5e82-333">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-333">Member</span></span> | <span data-ttu-id="e5e82-334">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-335">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-336">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-337">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-337">All</span></span> |
| <span data-ttu-id="e5e82-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="e5e82-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e5e82-339">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="e5e82-340">System. Security. Authentication. Kiedy</span><span class="sxs-lookup"><span data-stu-id="e5e82-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="e5e82-341">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-341">Member</span></span> | <span data-ttu-id="e5e82-342">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-343">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="e5e82-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="e5e82-344">System.Security.Policy</span></span>

| <span data-ttu-id="e5e82-345">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-345">Member</span></span> | <span data-ttu-id="e5e82-346">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-347">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="e5e82-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e5e82-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="e5e82-349">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-349">Member</span></span> | <span data-ttu-id="e5e82-350">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e5e82-351">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="e5e82-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e5e82-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="e5e82-353">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-353">Member</span></span> | <span data-ttu-id="e5e82-354">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-355">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="e5e82-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="e5e82-356">System.Threading</span></span>

| <span data-ttu-id="e5e82-357">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-357">Member</span></span> | <span data-ttu-id="e5e82-358">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-359">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-360">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="e5e82-361">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="e5e82-362">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="e5e82-363">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="e5e82-364">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="e5e82-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e5e82-365">System.Xml</span></span>

| <span data-ttu-id="e5e82-366">Członek</span><span class="sxs-lookup"><span data-stu-id="e5e82-366">Member</span></span> | <span data-ttu-id="e5e82-367">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="e5e82-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-368">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-369">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e5e82-370">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="e5e82-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="e5e82-371">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5e82-371">See also</span></span>

- [<span data-ttu-id="e5e82-372">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5e82-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="e5e82-373">Serializacja binarna w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5e82-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="e5e82-374">Analizator przenośności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e5e82-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
