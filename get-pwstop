#!/usr/bin/env pwsh
#requires -version 5
#
#
# The MIT License (MIT)
# Copyright (c) 2021 Stephen Preston and contributers
#
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.



<#PSScriptInfo
.VERSION 0.0.1
.GUID 1c26142a-da43-4125-9d70-97555cbb1752
.DESCRIPTION  This script is designed to act like linux top 
.AUTHOR Stephen Preston
.PROJECTURI 
.COMPANYNAME
.COPYRIGHT
.TAGS
.LICENSEURI
.ICONURI
.EXTERNALMODULEDEPENDENCIESforked 
.REQUIREDSCRIPTS
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
#>
<#
.SYNOPSIS
    Get-pwstop - is top for Windows in PowerShell 5+
.DESCRIPTION
     Get-pwstop is a command-line Processor and memory status utility for Windows written in PowerShell.
.PARAMETER help
    Display this help message.
.INPUTS
    System.String
.OUTPUTS
    System.String[]
.NOTES
    Run Get-sysdetails without arguments to view core functionality.
#>
[CmdletBinding()]
param(

)

function Activesysinfo{

 
    while ($null -eq $null) {

        $prochash = $null
        $memhash = $null
        $procdata = $null
        $memdata = $null
        $prochash = [ordered]@{}
        $memhash = @{}
        #Gather data required for command
        $procdata = Get-Counter -Counter '\Processor(*)\% Processor Time' | Select-Object -ExpandProperty CounterSamples 
        $memdata = (Get-Counter '\memory\% committed bytes in use' | Select-Object -ExpandProperty countersamples).Cookedvalue
    
        foreach ($procinfo in $procdata)
            {
                 $prochash.add($procinfo.InstanceName,[math]::Round(($procinfo.CookedValue),2))
            } 
            
            $memhash.add("Memory %",[math]::Round($memdata,2))
            
    
            clear-host
            Write-Host "Powershell TOP"
            New-Object psobject -Property  $prochash  
            New-Object psobject -Property  $memhash
        
            Start-Sleep -Seconds 2
    
     } 


}


Activesysinfo
