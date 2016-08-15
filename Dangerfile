
# Warn if touched files are missing the copyright header
copyright_header = "////Wire//Copyright(C)2016WireSwissGmbH////Thisprogramisfreesoftware:youcanredistributeitand/ormodify//itunderthetermsoftheGNUGeneralPublicLicenseaspublishedby//theFreeSoftwareFoundation,eitherversion3oftheLicense,or//(atyouroption)anylaterversion.////Thisprogramisdistributedinthehopethatitwillbeuseful,//butWITHOUTANYWARRANTY;withouteventheimpliedwarrantyof//MERCHANTABILITYorFITNESSFORAPARTICULARPURPOSE.Seethe//GNUGeneralPublicLicenseformoredetails.////YoushouldhavereceivedacopyoftheGNUGeneralPublicLicense//alongwiththisprogram.Ifnot,seehttp://www.gnu.org/licenses/.//"

touched = git.added_files | git.modified_files
paths = touched.select { |f| f.end_with? ".h", ".m", ".swift", ".mm" }
paths.each do |p|
  content = File.read(p).delete("\s").delete("\n")
  name = p.split('/').last
  warn "Missing copyright headers in #{name}" unless content.include? copyright_header
  warn "TODO comment left in #{name}" if content.downcase.include? "//todo"
end

# Warn if there are no labels attached to the PR
warn "Please add labels to this PR" if github.pr_labels.count == 0
