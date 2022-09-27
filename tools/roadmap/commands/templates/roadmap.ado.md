{{- /*gotype: github.com/SierraSoftworks/roadmap.Roadmap*/ -}}
{{ $root := . -}}

# {{ .Title }}

<div style="background: rgba(200, 200, 200, 0.15); padding: 1rem; margin-bottom: 2rem; overflow: auto;">
<div style="vertical-align: middle; font-size: 0.7rem; line-height: 1.8rem; float: left;">Authored by</div>
{{ range .Authors }}
<div style="margin-left: 1rem; padding-left: 1rem; border-left: 1px solid rgba(200, 200, 200, 0.5); float: left;">
    <h5 style="font-size: 0.8rem; margin: 0;">{{ .Name }}</h5>
    <p style="font-size: 0.6rem; margin: 0;">{{ .Contact }}</p>
</div>
{{ end }}
<div style="clear: both;"></div>
</div>


{{ .Description }}

## Important Dates

<div style="border-left: 4px solid gray; background: rgba(200, 200, 200, 0.15); padding: 1rem 2rem; text-align: center; margin: 2rem auto 2rem 8rem;">
{{ range .Timeline }}
<div style="text-align: left; padding-bottom: 1rem; margin-bottom: 1rem;">
<div style="margin-left: -9rem; margin-bottom: -0.3rem; height: 0; width: 5rem; font-size: 0.9rem; font-weight: 700; opacity: 0.7; text-align: right;">{{ .Date.Format "2006-01-02" }}</div>

<h3>{{ .Title }}</h3>
{{ .Description }}

</div>
{{ end }}
</div>

## Objectives
{{ range .Objectives }}
### {{ .Title }}
{{ .Description}}

{{ end }}

## Milestones

<div style="border-left: 4px solid gray; background: rgba(200, 200, 200, 0.15); padding: 1rem 2rem; text-align: center; margin: 2rem auto 2rem 7rem;">
{{ range $i,$m := .Milestones }}
<div style="text-align: left; padding-bottom: 1rem; margin-bottom: 1rem;">
<div style="margin-left: -8rem; margin-bottom: -0.3rem; text-align: right; height: 0; font-size: 0.9rem; font-weight: 700; opacity: 0.7; width: 4rem;">M{{ add $i 1 }}</div>
<h3>{{ $m.Title }}</h3>

{{ $m.Description }}

{{ range $m.Deliverables }}
<div style="position: relative; background-color: rgba(0, 0, 0, 0.1); margin: 2rem 0; padding: 10px 20px; border-left: 8px solid {{ .State | stateColor }};">
<h4 style="margin-top: 0; line-height: 1.8">
<span style="float: right; margin: 0;">{{ .State }}</span>

{{ .Title }}
{{ with .Requirement }}<span style="display: inline; font-size: 90%; padding: 3px 5px; background-color: {{ . | requirementColor }}; color: white; margin: 0 2px;"> {{ . }}</span>{{ end }}
</h4>

{{ .Description }}

{{ with .Reference }}[Read more &rarr;]({{ . }}){{ end }}
</div>
{{ end }}

</div>
{{ end }}
</div>
